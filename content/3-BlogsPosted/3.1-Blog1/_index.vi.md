---
title: "Blog 1"
date: 2026-07-05
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# SUBDOMAIN TAKEOVER: RỦI RO BẢO MẬT TIỀM ẨN TỪ DANGLING DNS

Hôm nay mình muốn tóm tắt và chia sẻ về một rủi ro bảo mật tuy không mới nhưng lại cực kỳ dễ mắc phải khi quản lý hạ tầng đám mây: **Subdomain Takeover (Chiếm quyền điều khiển tên miền phụ)**.

Khi triển khai các dự án, chúng ta thường tạo rất nhiều tài nguyên (S3 Bucket, CloudFront, Elastic Beanstalk...) và trỏ bản ghi DNS (như Route 53) về các tài nguyên này. Nhưng khi dự án kết thúc, nhiều anh em có thói quen chỉ dọn dẹp tài nguyên để tiết kiệm chi phí mà quên xóa các bản ghi DNS liên quan. Sự bất cẩn này vô tình tạo ra một lỗ hổng chết người để hacker lợi dụng.

![Normal Architecture](/images/3-blog/3.1-image1.png)

### Cơ chế của cuộc tấn công (Dangling DNS)

Quá trình này diễn ra vô cùng đơn giản nhưng lại để lại hậu quả nghiêm trọng về uy tín thương hiệu:

1. **Bản ghi mồ côi:** Một bản ghi CNAME trong hệ thống DNS (VD: `promo.company.com`) trỏ đến một S3 bucket hoặc môi trường Beanstalk (`promo-campaign.s3.amazonaws.com`).

![Route 53 Routing](/images/3-blog/3.1-image2.png)

2. **Xóa tài nguyên nhưng giữ DNS:** Quản trị viên xóa bucket `promo-campaign` khi chiến dịch kết thúc, nhưng quên không xóa bản ghi CNAME. Lúc này `promo.company.com` đang trỏ vào một khoảng không (Dangling DNS).

![Deleted Resource](/images/3-blog/3.1-image3.png)

3. **Kẻ tấn công "nhặt" lại:** Hacker liên tục dò quét (scan) các tên miền phụ. Khi phát hiện bản ghi đang trỏ vào một tài nguyên AWS không tồn tại, chúng ngay lập tức vào tài khoản AWS của chúng và khởi tạo một tài nguyên mới (ví dụ S3 bucket) với đúng tên mà bạn đã xóa (`promo-campaign`).
4. **Chiếm quyền hoàn tất:** Giờ đây, khi khách hàng truy cập vào `promo.company.com`, họ sẽ bị dẫn tới nội dung hoàn toàn do hacker kiểm soát (trang web lừa đảo đăng nhập, phát tán mã độc, hoặc qua mặt CORS để đánh cắp cookie).

![Subdomain Takeover Complete](/images/3-blog/3.1-image4.png)

### Những điểm nổi bật để phòng chống (Best Practices)

Thay vì phụ thuộc vào trí nhớ của con người, AWS khuyến nghị các phương pháp tiếp cận tự động và có hệ thống:

* **Quy trình dọn dẹp đồng bộ (Lifecycle Management):** Nguyên tắc vàng trong vận hành là luôn xóa bản ghi DNS (Route 53) trước hoặc cùng lúc với việc xóa hoặc giải phóng tài nguyên đích (S3, CloudFront, ELB, EC2 Elastic IP). Đừng bao giờ để DNS "treo".
* **Sử dụng Alias Records thay cho CNAME:** Trên AWS Route 53, hãy ưu tiên sử dụng Alias Record để trỏ nội bộ giữa các dịch vụ AWS. Dù Alias record không ngăn chặn 100% Subdomain Takeover, nhưng nó được quản lý chặt chẽ hơn và tích hợp sâu với vòng đời của các tài nguyên AWS so với CNAME truyền thống.
* **Tận dụng các bản cập nhật bảo mật của AWS:** AWS đã liên tục tung ra các cơ chế bảo vệ ngầm. Ví dụ, với CloudFront hiện tại, kẻ tấn công rất khó để chiếm đoạt tên miền chéo tài khoản vì CloudFront yêu cầu phải có chứng chỉ TLS/SSL hợp lệ hoặc phải vượt qua bước xác minh quyền sở hữu domain (Domain Ownership Verification).
* **Giám sát tự động hóa:** Thiết lập các rule trong AWS Config hoặc bắt sự kiện qua Amazon EventBridge để cảnh báo ngay lập tức nếu phát hiện một bản ghi Route 53 đang trỏ đến một tài nguyên không còn tồn tại trong tài khoản.

![Automated Monitoring Architecture](/images/3-blog/3.1-image5.png)

### Kết luận và Kiến nghị

Subdomain Takeover là minh chứng rõ ràng cho việc lỗi cấu hình (misconfiguration) có thể gây ra hậu quả tàn khốc ngang ngửa với các cuộc tấn công kỹ thuật cao. Bảo mật đám mây không chỉ là xây dựng tường lửa chống xâm nhập từ bên ngoài, mà còn là quản trị vòng đời tài nguyên (Resource Lifecycle) chặt chẽ và sạch sẽ từ bên trong.

**Kiến nghị:** Theo ý kiến cá nhân của mình, đối với các hệ thống có hàng trăm subdomain, các bạn làm DevOps/SecOps nên chủ động viết các script tự động (dùng Python/Boto3) chạy định kỳ bằng AWS Lambda. Script này sẽ làm nhiệm vụ dò quét toàn bộ Hosted Zone trong Route 53, đối chiếu với danh sách các tài nguyên đang thực sự chạy. Nếu phát hiện DNS "mồ côi", hệ thống có thể tự động bắn cảnh báo qua Slack/Telegram hoặc tự động gỡ luôn bản ghi đó để triệt tiêu rủi ro tức thì.

---
**Nguồn tham khảo:**
*   [AWS Study Group VN | Subdomain Takeover Chiếm quyền điều khiển tên miền phụ](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2202705877161039)
*   [Threat tactic spotlight: Subdomain takeover | AWS Security Blog](https://aws.amazon.com/blogs/security/threat-tactic-spotlight-subdomain-takeover/)