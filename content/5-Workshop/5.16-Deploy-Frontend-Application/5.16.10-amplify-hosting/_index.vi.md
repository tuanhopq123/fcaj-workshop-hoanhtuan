---
title : "Tạo ứng dụng AWS Amplify Hosting"
date : 2026-07-05
weight : 10
chapter : false
pre : " <b> 5.16.10 </b> "
---

1. **Mở AWS Amplify**
   * Vào **AWS Amplify → Deploy an app**.
   * Chọn **GitHub**.

![Chọn nguồn source code](/images/5-Workshop/5.16/pic3.png)

2. **Cấp quyền cho repository**
   * Bấm **Next**.
   * Cấp quyền cho repository: `energy-waste-dashboard`.

3. **Chọn repository và branch**
   * Bấm **Next**.
   * Repository: `energy-waste-dashboard`
   * Branch: `main`

![Add repository and branch](/images/5-Workshop/5.16/pic4.png)

4. **Cấu hình App settings**

   | Setting | Giá trị |
   |---|---|
   | App name | `energy-waste-dashboard` |
   | Framework | Next.js |
   | Frontend build command | `npm run build` |
   | Build output directory | `.next` |
   | Service role | Create and use a new service role |
   | Build image | Amazon Linux 2023 |

![App settings](/images/5-Workshop/5.16/pic5.png)

5. **Thêm biến môi trường (Advanced settings)**

   | Key | Value |
   |---|---|
   | `NEXT_PUBLIC_AWS_REGION` | `ap-southeast-1` |
   | `NEXT_PUBLIC_COGNITO_USER_POOL_ID` | `ap-southeast-1_OiGmvapoL` |
   | `NEXT_PUBLIC_COGNITO_CLIENT_ID` | `42bod21u3a1g499u643mt056fm` |
   | `NEXT_PUBLIC_API_BASE_URL` | `https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com` |

![Advanced settings và environment variables](/images/5-Workshop/5.16/pic6.png)

6. **Xem lại và deploy**
   * Bấm **Next**, kiểm tra lại cấu hình, sau đó bấm **Save and deploy**.

![Review](/images/5-Workshop/5.16/pic7.png)

Sau khi build xong, app sẽ xuất hiện tại trang Overview với branch đã deploy và domain URL.

![App overview sau khi deploy](/images/5-Workshop/5.16/pic8.png)
