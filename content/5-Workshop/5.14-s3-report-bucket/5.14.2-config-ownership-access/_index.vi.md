---
title : "Cấu hình quyền sở hữu và Public Access"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.14.2. </b> "
---

#### Object Ownership

Tại phần **Object Ownership**, giữ nguyên thiết lập mặc định:
- **ACLs disabled (Bucket owner enforced)**

*Lưu ý: Không bật ACL. Với thiết lập "Bucket owner enforced", ACL bị vô hiệu hóa và quyền truy cập được quản lý bằng IAM hoặc bucket policy. Đây cũng là thiết lập mặc định của bucket general purpose mới.*

#### Block Public Access

Tại phần **Block Public Access settings for this bucket**, giữ bật:
- **Block all public access**

*Lưu ý: Bốn lựa chọn bên dưới phải tiếp tục được đánh dấu. Không bỏ chọn và không xác nhận cho phép public access. AWS khuyến nghị giữ toàn bộ Block Public Access bật cho các bucket không có nhu cầu công khai; thiết lập này có thể chặn bucket policy hoặc ACL cố gắng mở quyền public.*

#### Bucket Versioning

Tại **Bucket Versioning**, chọn: **Disable**

*Lưu ý: Project hiện chưa cần lưu nhiều phiên bản của cùng một file báo cáo. Mỗi báo cáo sẽ có object key theo ngày nên chưa cần bật versioning.*

#### Tags

- Có thể để trống.
- Hoặc thêm tag để dễ quản lý (không bắt buộc):
  - **Key**: `Project`
  - **Value**: `EnergyWasteMonitoring`