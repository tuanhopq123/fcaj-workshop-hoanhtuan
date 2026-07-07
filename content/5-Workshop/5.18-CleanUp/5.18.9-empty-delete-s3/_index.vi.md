---
title: "5.18.9. Làm rỗng và Xóa Amazon S3 Report Bucket"
date: 2026-07-07
weight: 9
---

S3 chỉ cho phép xóa bucket sau khi bucket đó đã hoàn toàn trống rỗng. Thao tác Empty sẽ xóa vĩnh viễn toàn bộ object bên trong và không thể khôi phục lại.

#### Bước 1: Làm rỗng Bucket (Empty Bucket)
1. Truy cập vào S3 Console, quay lại danh sách **General purpose buckets**.
2. Đánh dấu tích chọn vào bucket chứa báo cáo dự án của bạn.
3. Chọn nút **Empty**.
4. Kiểm tra lại thông tin, nhập chính xác chuỗi văn bản xác nhận và chọn **Empty**.
5. Chờ trang trạng thái hiển thị quá trình dọn dẹp hoàn tất. Tuyệt đối không đóng trang khi hệ thống đang xử lý object.

![Làm rỗng S3 Bucket](/images/5-Workshop/5.18-CleanUp/Picture5.png)
![Trạng thái làm rỗng thành công](/images/5-Workshop/5.18-CleanUp/Picture6.png)

#### Bước 2: Thực thi xóa hẳn Bucket
1. Quay lại giao diện danh sách bucket hệ thống.
2. Đánh dấu tích chọn vào bucket báo cáo đã được làm rỗng và bấm nút **Delete**.
3. Nhập chính xác tên của bucket để xác thực bảo mật.
4. Chọn **Delete bucket** và kiểm tra đảm bảo thực thể không còn xuất hiện trong danh sách.

![Cấu hình xóa S3 Bucket](/images/5-Workshop/5.18-CleanUp/Picture7.png)
![Hệ thống S3 đã dọn dẹp xong bucket](/images/5-Workshop/5.18-CleanUp/Picture8.png)