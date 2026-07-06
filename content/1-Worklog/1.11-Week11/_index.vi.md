---
title: "Nhật ký công việc Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Nội dung dưới đây chỉ mang tính chất tham khảo. Vui lòng **không sao chép nguyên văn** vào báo cáo của bạn, bao gồm cả phần lưu ý này.
{{% /notice %}}

## Mục tiêu tuần

* Triển khai module **Report Generator** theo kiến trúc Serverless trên AWS.
* Tích hợp AWS Lambda với Amazon DynamoDB và Amazon S3.
* Tăng cường bảo mật IAM theo nguyên tắc **Least Privilege**.
* Tập trung hoàn thiện mã nguồn và cấu hình thực tế thay vì thực hiện thêm các bài Lab mới.

---

## Công việc đã thực hiện

| Công việc | Kết quả |
|-----------|----------|
| Cấu hình AWS Lambda | Tạo hàm **energy-report-generator** sử dụng Python. Tối ưu bộ nhớ (Memory) và thời gian thực thi (Timeout) nhằm cải thiện hiệu năng xử lý báo cáo đồng thời tối ưu chi phí vận hành. |
| Thiết lập Environment Variables | Cấu hình các biến môi trường cho bảng DynamoDB, bucket Amazon S3, tiền tố lưu báo cáo và các tham số hệ thống nhằm loại bỏ việc hard-code trong mã nguồn và thuận tiện khi triển khai nhiều môi trường khác nhau. |
| Cấu hình bảo mật IAM | Thiết lập IAM Execution Role theo nguyên tắc **Least Privilege**, chỉ cấp các quyền cần thiết như DynamoDB Query, PutItem, Amazon S3 PutObject và CloudWatch Logs cho Lambda. |
| Xây dựng quy trình tạo báo cáo | Hoàn thiện luồng xử lý tự động: AWS Lambda truy vấn dữ liệu từ DynamoDB, sinh báo cáo định dạng JSON và lưu trực tiếp lên Amazon S3. |
| Rà soát bảo mật | Kiểm tra lại quyền truy cập, cấu hình Lambda và chiến lược ghi log nhằm đảm bảo module đáp ứng các khuyến nghị bảo mật của AWS. |

---

## Kết quả đạt được

* Hoàn thành module **Report Generator** theo kiến trúc Serverless.
* Tích hợp thành công AWS Lambda, Amazon DynamoDB và Amazon S3 trong quy trình tạo báo cáo tự động.
* Loại bỏ hoàn toàn các cấu hình hard-code bằng cách sử dụng Environment Variables.
* Áp dụng nguyên tắc **Least Privilege** để tăng cường bảo mật cho hệ thống.
* Nâng cao kỹ năng triển khai ứng dụng Serverless và quản lý bảo mật trên nền tảng AWS.

---

## Đánh giá

* Hoàn thành đầy đủ các mục tiêu đề ra trong Tuần 11.
* Module Report Generator đã sẵn sàng để tích hợp vào hệ thống và đáp ứng các tiêu chuẩn triển khai Serverless trên AWS.
* Kiến thức về AWS Lambda, IAM và Amazon S3 được vận dụng hiệu quả để xây dựng một giải pháp có tính bảo mật, dễ bảo trì và thuận tiện mở rộng trong tương lai.

---

## Kế hoạch tuần tới

* Kiểm thử toàn bộ hệ thống theo quy trình End-to-End.
* Chuẩn bị slide thuyết trình và demo dự án.
* Hoàn thiện tài liệu triển khai, mã nguồn và các script dọn dẹp tài nguyên AWS.
* Tổng rà soát kiến trúc hệ thống trước khi hoàn thành và bàn giao dự án.