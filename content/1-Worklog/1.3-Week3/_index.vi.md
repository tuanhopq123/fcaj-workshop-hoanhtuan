---
title: "Nhật ký công việc Tuần 3"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---


## Mục tiêu Tuần 3

- Thiết lập nền tảng bảo mật cho hệ thống bằng AWS IAM.
- Khởi tạo cơ sở dữ liệu Amazon DynamoDB phục vụ dự án Smart Home Energy Waste Monitoring & Alert System.
- Hoàn thành các bài thực hành AWS IAM, Amazon VPC và AWS Budget.

---

## Công việc thực hiện trong tuần

| Ngày | Công việc                                                                                                        | Ngày bắt đầu | Ngày hoàn thành |
| ---- | ---------------------------------------------------------------------------------------------------------------- | ------------ | --------------- |
| 1    | Cấu hình IAM User, IAM Role và IAM Policy cho hệ thống theo nguyên tắc Least Privilege.                          | 01/05/2026   | 01/05/2026      |
| 2    | Khởi tạo các bảng DynamoDB gồm Rooms, Telemetry, Alerts và Reports, đồng thời thêm dữ liệu mẫu phục vụ kiểm thử. | 02/05/2026   | 02/05/2026      |
| 3    | Hoàn thành bài thực hành AWS IAM và thực hành quản lý User, Group, Role và Policy.                               | 03/05/2026   | 03/05/2026      |
| 4    | Hoàn thành bài thực hành Amazon VPC để tìm hiểu về VPC, Subnet, Route Table, Internet Gateway và NAT Gateway.    | 04/05/2026   | 04/05/2026      |
| 5    | Hoàn thành bài thực hành AWS Budget và rà soát lại kiến trúc hệ thống, cấu hình IAM và cơ sở dữ liệu.            | 05/05/2026   | 05/05/2026      |


---

## Kết quả đạt được

Trong tuần này, em tập trung xây dựng nền tảng bảo mật và cơ sở dữ liệu cho hệ thống, đồng thời hoàn thành các bài thực hành quan trọng về AWS.

### Tiến độ dự án

Hệ thống đã hoàn thành bước thiết lập bảo mật bằng **AWS IAM**.

Các **IAM Role** và **IAM Policy** được cấu hình theo nguyên tắc **Least Privilege (Quyền tối thiểu)** nhằm đảm bảo mỗi dịch vụ chỉ được cấp đúng quyền cần thiết để thực hiện chức năng của mình.

Quyền truy cập được cấu hình cho AWS Lambda bao gồm:

- Truy cập các bảng Amazon DynamoDB.
- Ghi log lên Amazon CloudWatch.
- Truy cập Amazon S3 để lưu trữ và đọc báo cáo (khi cần).

Bên cạnh đó, cơ sở dữ liệu **Amazon DynamoDB** cũng được khởi tạo để phục vụ hệ thống giám sát điện năng.

Các bảng dữ liệu ban đầu bao gồm:

- **Rooms** – Lưu thông tin các phòng.
- **Telemetry** – Lưu dữ liệu cảm biến ảo.
- **Alerts** – Lưu các cảnh báo lãng phí điện.
- **Reports** – Lưu thông tin báo cáo tiêu thụ điện.

Dữ liệu mẫu đã được thêm vào các bảng nhằm chuẩn bị cho quá trình phát triển API và kiểm thử trong các tuần tiếp theo.

---

# Thực hành AWS

## Lab 2 — AWS IAM

Trong bài thực hành này, em tìm hiểu về dịch vụ **AWS Identity and Access Management (IAM)** và thực hiện quản lý người dùng cũng như phân quyền truy cập.

Các nội dung đã thực hiện gồm:

- Tạo IAM Group.
- Tạo IAM User.
- Gán quyền thông qua IAM Policy.
- Kích hoạt xác thực đa yếu tố (MFA).
- Kiểm tra và xác minh cấu hình bảo mật.

![Tạo IAM Group](/images/1-worklog/1.3-lab2-1.png)

![Tạo IAM User](/images/1-worklog/1.3-lab2-2.png)

![Gán quyền truy cập](/images/1-worklog/1.3-lab2-3.png)

![Cấu hình IAM Policy](/images/1-worklog/1.3-lab2-4.png)

![Bật MFA](/images/1-worklog/1.3-lab2-5.png)

![Hoàn thành Lab IAM](/images/1-worklog/1.3-lab2-6.png)

---

## Lab 3 — Amazon VPC

Bài thực hành giúp em hiểu rõ cách xây dựng một hệ thống mạng riêng trên AWS bằng **Amazon Virtual Private Cloud (VPC)**.

Các bước thực hiện bao gồm:

- Tạo VPC.
- Cấu hình CIDR Block.
- Tạo Public Subnet và Private Subnet.
- Cấu hình Route Table.
- Tạo Internet Gateway.
- Cấu hình NAT Gateway.
- Kiểm tra khả năng kết nối giữa các thành phần trong hệ thống.

![Lab VPC 1](/images/1-worklog/1.3-lab3-1.png)

![Lab VPC 2](/images/1-worklog/1.3-lab3-2.png)

![Lab VPC 3](/images/1-worklog/1.3-lab3-3.png)

![Lab VPC 4](/images/1-worklog/1.3-lab3-4.png)

![Lab VPC 5](/images/1-worklog/1.3-lab3-5.png)

![Lab VPC 6](/images/1-worklog/1.3-lab3-6.png)

![Lab VPC 7](/images/1-worklog/1.3-lab3-7.png)

![Lab VPC 8](/images/1-worklog/1.3-lab3-8.png)

![Lab VPC 9](/images/1-worklog/1.3-lab3-9.png)

![Lab VPC 10](/images/1-worklog/1.3-lab3-10.png)

![Lab VPC 11](/images/1-worklog/1.3-lab3-11.png)

![Lab VPC 12](/images/1-worklog/1.3-lab3-12.png)

![Lab VPC 13](/images/1-worklog/1.3-lab3-13.png)

![Lab VPC 14](/images/1-worklog/1.3-lab3-14.png)

![Lab VPC 15](/images/1-worklog/1.3-lab3-15.png)

![Lab VPC 16](/images/1-worklog/1.3-lab3-16.png)

![Lab VPC 17](/images/1-worklog/1.3-lab3-17.png)

![Lab VPC 18](/images/1-worklog/1.3-lab3-18.png)

![Lab VPC 19](/images/1-worklog/1.3-lab3-19.png)

![Lab VPC 20](/images/1-worklog/1.3-lab3-20.png)

![Lab VPC 21](/images/1-worklog/1.3-lab3-21.png)

![Lab VPC 22](/images/1-worklog/1.3-lab3-22.png)

![Lab VPC 23](/images/1-worklog/1.3-lab3-23.png)

---

## Lab 7 — AWS Budget

Bài thực hành giúp em làm quen với việc quản lý chi phí trên nền tảng AWS.

Các nội dung thực hiện gồm:

- Tạo Cost Budget.
- Thiết lập ngưỡng cảnh báo.
- Cấu hình gửi email thông báo khi vượt ngưỡng.
- Theo dõi mức sử dụng AWS Credits.
- Kiểm tra hoạt động của Budget.

![AWS Budget 1](/images/1-worklog/1.3-lab7-1.png)

![AWS Budget 2](/images/1-worklog/1.3-lab7-2.png)

![AWS Budget 3](/images/1-worklog/1.3-lab7-3.png)

![AWS Budget 4](/images/1-worklog/1.3-lab7-4.png)

![AWS Budget 5](/images/1-worklog/1.3-lab7-5.png)

---

## Kiến thức thu nhận được

Sau khi hoàn thành các công việc trong tuần, em đã hiểu rõ hơn về:

- Quản lý danh tính và phân quyền bằng AWS IAM.
- Thiết kế quyền truy cập theo nguyên tắc Least Privilege.
- Kiến thức nền tảng về mạng trên AWS với Amazon VPC.
- Quản lý và tối ưu chi phí bằng AWS Budget.
- Khởi tạo và quản lý cơ sở dữ liệu NoSQL bằng Amazon DynamoDB.

---

## Tổng kết Tuần 3

- Hoàn thành cấu hình bảo mật cho hệ thống.
- Khởi tạo cơ sở dữ liệu Amazon DynamoDB.
- Hoàn thành Lab AWS IAM.
- Hoàn thành Lab Amazon VPC.
- Hoàn thành Lab AWS Budget.

---

## Kế hoạch Tuần tiếp theo

- Phát triển các hàm AWS Lambda.
- Xây dựng các REST API cho hệ thống.
- Kết nối AWS Lambda với Amazon DynamoDB.
- Thực hiện kiểm thử các chức năng CRUD.