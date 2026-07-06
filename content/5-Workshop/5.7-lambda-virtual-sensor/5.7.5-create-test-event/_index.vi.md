---
title: "5.7.5. Khởi Tạo Sự Kiện Kiểm Thử (Test Event)"
date: 2026-07-05
weight: 5
---

Để kiểm tra tính đúng đắn của logic xử lý lãng phí điện năng, chúng ta cần tạo một Test Event truyền thuộc tính ép buộc trạng thái (`forceWaste`).

1. Tại giao diện hàm Lambda, chuyển sang tab **Test** và chọn **Create new event**.
2. Thiết lập thông số cấu hình cho Test Event như sau *(Xem hình minh họa chi tiết tại tệp `05-test-event-force-waste.png`)*:
   ![Tạo test event mới](/images/5-Workshop/5.7-lambda-virtual-sensor/image_c48594.png)
   * **Event sharing settings**: Chọn `Private`.
   * **Event name**: Nhập `manual_force_waste_test`.
   * **Event JSON**: Xóa định dạng mẫu mặc định và điền khối JSON sau:
  ![Kết quả kiểm tra hàm Lambda thành công](/images/5-Workshop/5.7-lambda-virtual-sensor/06-ket-qua-test-virtual-sensor.png)
```json
{
  "source": "manual-test",
  "forceWaste": true
}