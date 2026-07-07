---
title: "Blogs Posted"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 3. </b> "
---
This section will list and introduce the technical blogs I have shared regarding cloud security, data engineering automation, and identity management on AWS.

###  [Blog 1 - SUBDOMAIN TAKEOVER: RỦI RO BẢO MẬT TỪ CÁC BẢN GHI DNS "MỒ CÔI" TRÊN AWS](3.1-Blog1/)
Bài viết cảnh báo về lỗ hổng nguy hiểm mang tên Subdomain Takeover (Chiếm quyền điều khiển tên miền phụ) phát sinh từ các bản ghi DNS mồ côi (Dangling DNS) sau khi hủy bỏ tài nguyên AWS (như S3, CloudFront) mà quên xóa bản ghi Route 53. Đồng thời, bài viết chia sẻ các giải pháp phòng ngừa cốt lõi bao gồm đồng bộ quy trình dọn dẹp tài nguyên, ưu tiên dùng Alias Records và xây dựng script kiểm tra tự động định kỳ thông qua AWS Lambda.

###  [Blog 2 - TỰ ĐỘNG HÓA TROUBLESHOOTING DMS MIGRATION (ORACLE ➡️ REDSHIFT) VỚI AWS DEVOPS AGENT](3.2-Blog2/)
Nội dung bài viết tập trung giải quyết bài toán tối ưu quy trình tìm nguyên nhân gốc rễ (RCA) khi pipeline dịch chuyển dữ liệu lớn gặp sự cố hoặc độ trễ cao. Giải pháp đề xuất là kết hợp giám sát truyền thống của CloudWatch Alarms với các tác vụ tự động hóa từ EventBridge, Lambda và AWS DevOps Agent giúp hệ thống chủ động điều tra logs/metrics sâu bên trong hệ thống Oracle/Redshift, tự động đưa ra kịch bản xử lý lỗi nhanh chóng.

###  [Blog 3 - BẢO MẬT AI AGENT TRÊN AWS VỚI AUTH0 VÀ AMAZON BEDROCK AGENTCORE](3.3-Blog3/)
Bài viết phân tích các thách thức bảo mật khi triển khai AI Agent và giới thiệu giải pháp kết hợp giữa Auth0 và Amazon Bedrock AgentCore. Bằng cách áp dụng mô hình kiến trúc Identity-First, hệ thống giúp kiểm soát chặt chẽ danh tính người dùng qua OIDC, quản lý token "just-in-time" bằng Auth0 Token Vault, phân quyền động (FGA) và tích hợp cơ chế phê duyệt từ con người (Human-in-the-loop) để đảm bảo an toàn tối đa cho môi trường Production.