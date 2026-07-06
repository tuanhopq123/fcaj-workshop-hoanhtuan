---
title: "5.7.6. Thực Thi Thử Nghiệm Và Kiểm Tra Kết Quả"
date: 2026-07-05
weight: 6
---

1. Tại khu vực danh sách chọn Test Event, chỉ định đúng sự kiện vừa tạo: `manual_force_waste_test`.
2. Bấm nút **Test**.
3. Hệ thống tiến hành thực thi hàm Lambda. Khi kết thúc xử lý, tab **Execution result** sẽ hiển thị nội dung phản hồi. Định dạng dữ liệu đầu ra cần đảm bảo trả về thành công mã `statusCode: 200`, thông điệp `"Telemetry published successfully"`, đồng thời ghi nhận kịch bản `"scenario": "waste"` đúng như yêu cầu kiểm thử.