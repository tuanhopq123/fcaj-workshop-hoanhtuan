---
title: "5.18.11. Xóa CloudWatch Log Groups"
date: 2026-07-07
weight: 11
---

Hành vi gỡ bỏ Lambda function không tự động dọn dẹp các Log Group đã tạo phát sinh kèm theo. Bạn cần thực hiện gỡ bỏ Log Group thủ công trong dịch vụ CloudWatch Logs.

1. Tìm kiếm cụm từ **CloudWatch** và mở trang quản trị hệ thống.
2. Trong danh mục phân nhánh bên trái, chọn **Logs** $\rightarrow$ **Log groups**.
3. Tìm kiếm và đánh dấu tích chọn vào năm Log Group sau:
   * `/aws/lambda/energy-waste-detector`
   * `/aws/lambda/energy-virtual-sensor`
   * `/aws/lambda/energy-api-handler`
   * `/aws/lambda/energy-report-generator`
   * `/aws/amplify/d2ppdnlr5ik3e8`
4. Chọn thanh công cụ **Actions** $\rightarrow$ **Delete log group(s)**.

![Chọn CloudWatch Log Groups](/images/5-Workshop/5.18-CleanUp/Picture11.png)

5. Kiểm tra kỹ lưỡng lại danh sách bản ghi và xác nhận bấm chọn **Delete**.

![Xác nhận xóa Log Groups](/images/5-Workshop/5.18-CleanUp/Picture12.png)