---
title: "Blog 3"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 3.3. </b> "
---


# BẢO MẬT AI AGENT TRÊN AWS VỚI AUTH0 VÀ AMAZON BEDROCK AGENTCORE

Khi các AI Agent ngày càng thông minh và có khả năng thực hiện nhiều tác vụ như đọc email, đặt lịch họp, truy cập hệ thống CRM hoặc gọi các dịch vụ API thay cho người dùng, vấn đề bảo mật cũng trở nên quan trọng hơn bao giờ hết. Một AI Agent càng có nhiều quyền thì càng trở thành mục tiêu hấp dẫn đối với các cuộc tấn công mạng.

Việc sử dụng Shared API Key hoặc lưu trữ trực tiếp thông tin xác thực trong mã nguồn tiềm ẩn rất nhiều rủi ro. Chỉ cần một lỗ hổng nhỏ, toàn bộ hệ thống có thể bị khai thác. Để giải quyết vấn đề này, AWS kết hợp với Auth0 xây dựng mô hình trong đó mỗi AI Agent đều sở hữu một danh tính (Identity) riêng và được xác thực, phân quyền giống như một người dùng thực sự.

Khác với các ứng dụng truyền thống, AI Agent không hoạt động theo những quy trình cố định mà có khả năng tự suy luận và lựa chọn công cụ cần sử dụng. Nếu các Access Token được đưa trực tiếp vào quá trình suy luận, chúng có thể bị lộ hoặc bị khai thác ngoài ý muốn. Đồng thời, mô hình phân quyền theo vai trò (RBAC) truyền thống cũng không còn đủ linh hoạt để đáp ứng các nhu cầu thay đổi liên tục của AI Agent.

Để khắc phục những hạn chế đó, AWS giới thiệu giải pháp kết hợp giữa **Amazon Bedrock AgentCore** và **Auth0 for AI Agents**, đưa quản lý định danh và quyền truy cập (Identity and Access Management) trở thành nền tảng cốt lõi trong việc bảo mật các hệ thống AI Agent.

## Những điểm nổi bật của giải pháp

### Xác thực người dùng bằng OpenID Connect (OIDC)

Trước khi AI Agent có thể thực hiện bất kỳ hành động nào, hệ thống cần xác minh chính xác danh tính của người gửi yêu cầu. Amazon Bedrock AgentCore tích hợp với Auth0 thông qua chuẩn OpenID Connect (OIDC), giúp người dùng đăng nhập an toàn và kế thừa các cơ chế bảo mật như xác thực đa yếu tố (MFA).

### Cấp quyền Just-in-Time với Auth0 Token Vault

Khi AI Agent cần truy cập các dịch vụ bên ngoài như Google Calendar hoặc CRM, Auth0 Token Vault sẽ cấp phát Access Token ngay tại thời điểm cần sử dụng. Token chỉ được cấp đúng phạm vi quyền của người dùng và không bị lộ trong quá trình AI Agent suy luận, giúp giảm thiểu nguy cơ rò rỉ thông tin xác thực.

### Mô hình Zero-Trust giữa các AI Agent

Thay vì mặc định tin tưởng các AI Agent trong cùng hệ thống, Auth0 áp dụng mô hình Zero-Trust bằng cách sử dụng Machine-to-Machine Token. Mọi giao tiếp giữa Supervisor Agent và Sub-Agent đều phải được xác thực theo chuẩn Agent-to-Agent (A2A) trước khi được phép trao đổi dữ liệu.

### Kiểm soát truy cập công cụ với AgentCore Gateway

Tất cả các yêu cầu từ AI Agent đến các dịch vụ bên ngoài đều phải đi qua Amazon Bedrock AgentCore Gateway. Gateway sẽ kiểm tra chữ ký số, thời hạn sử dụng và đối tượng của Access Token do Auth0 cấp trước khi cho phép AI Agent truy cập các công cụ hoặc API bên ngoài.

### Phân quyền động và Human-in-the-Loop

Auth0 Fine-Grained Authorization (FGA) giúp đánh giá quyền truy cập theo thời gian thực thay vì chỉ dựa trên các vai trò cố định. Đối với những thao tác có mức độ rủi ro cao, cơ chế Client Initiated Backchannel Authentication (CIBA) sẽ tạm dừng AI Agent và yêu cầu người dùng xác nhận trước khi tiếp tục thực hiện, giúp tăng cường tính an toàn cho hệ thống.

## Kết luận

Để xây dựng một AI Agent an toàn, việc sử dụng các mô hình AI mạnh là chưa đủ mà còn cần một nền tảng quản lý định danh đáng tin cậy. Thay vì tự phát triển các cơ chế xác thực và phân quyền riêng, nhà phát triển có thể tận dụng sự kết hợp giữa Auth0 và Amazon Bedrock AgentCore để tập trung vào việc xây dựng các tính năng của AI Agent, đồng thời vẫn đảm bảo các tiêu chuẩn bảo mật ở cấp doanh nghiệp.

Trong bối cảnh AI Agent ngày càng được ứng dụng rộng rãi trong doanh nghiệp, việc áp dụng kiến trúc **Identity-First** sẽ giúp hệ thống vừa đảm bảo tính linh hoạt, vừa duy trì khả năng mở rộng và an toàn khi đưa vào môi trường Production.

## Kiến nghị

Trong bài viết tiếp theo, mình sẽ trình bày chi tiết hơn về cách triển khai thực tế **Auth0 Token Vault** và **Client Initiated Backchannel Authentication (CIBA)** trên nền tảng AWS. Theo mình, đây là hai tính năng nổi bật nhất vì giúp AI Agent vận hành an toàn hơn và đáp ứng các yêu cầu bảo mật trong môi trường Production.

## Hình ảnh minh họa

![Tổng quan kiến trúc](/images/3-blog/3.4-image1.png)

![Luồng xác thực người dùng](/images/3-blog/3.4-image2.png)

![Quy trình hoạt động của Token Vault](/images/3-blog/3.4-image3.png)

![Kiến trúc bảo mật với Amazon Bedrock AgentCore](/images/3-blog/3.4-image4.png)

## Tài liệu tham khảo

https://www.facebook.com/groups/660548818043427/?multi_permalinks=2204747060290254&ref=share

## Hướng dẫn

https://aws.amazon.com/vi/blogs/apn/securing-enterprise-ready-ai-agents-with-auth0-for-ai-agents-and-amazon-bedrock-agentcore/