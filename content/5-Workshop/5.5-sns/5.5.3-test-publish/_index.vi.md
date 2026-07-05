---
title: "5.5.3 Thử nghiệm xuất bản dữ liệu (Publish Message)"
weight: 3
description: "Mô phỏng phát tín hiệu cảnh báo lãng phí năng lượng dạng JSON và rà soát kết quả thư nhận được."
---

# 5.5.3 Test gửi email cảnh báo hệ thống

Nhằm đảm bảo luồng tin tức luân chuyển chính xác, chúng ta sẽ thực hiện kiểm thử thủ công tính năng xuất bản thông điệp trực tiếp từ bảng điều khiển quản trị[cite: 2].

### Các bước thực hiện:

1. Tại màn hình làm việc của topic `energy-waste-alert-topic`, nhấn chọn nút **Publish message** ở góc bên phải[cite: 2].
2. Trong hộp thoại cấu hình chi tiết thông điệp (Message details), thiết lập tiêu đề thư[cite: 2]:
   * **Subject - optional:** `Test energy waste alert`[cite: 2]
3. Di chuyển tiếp đến phần cấu hình thân bài viết (**Message body**)[cite: 2]:
   * Chọn cấu hình mặc định: **Identical payload for all delivery protocols**[cite: 2].
   * Sao chép đoạn mã JSON mô phỏng gói tin sự kiện lãng phí điện năng của phòng thiết bị dưới đây và dán vào ô nhập liệu[cite: 2]:

```json
{
  "alertType": "ENERGY_WASTE",
  "roomId": "lab-01",
  "deviceId": "aircon-01",
  "deviceStatus": "ON",
  "occupancy": false,
  "powerW": 180,
  "message": "Test alert from Amazon SNS for Smart Home Energy Waste Monitoring System."
}