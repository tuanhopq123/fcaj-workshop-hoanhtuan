---
title : "Create the AWS Amplify Hosting App"
date : 2026-07-05
weight : 10
chapter : false
pre : " <b> 5.16.10 </b> "
---

1. **Open AWS Amplify**
   * Go to **AWS Amplify → Deploy an app**.
   * Choose **GitHub**.

![Choose source code provider](/images/5-Workshop/5.16/pic3.png)

2. **Grant repository access**
   * Click **Next**.
   * Grant access to the repository: `energy-waste-dashboard`.

3. **Select repository and branch**
   * Click **Next**.
   * Repository: `energy-waste-dashboard`
   * Branch: `main`

![Add repository and branch](/images/5-Workshop/5.16/pic4.png)

4. **Configure app settings**

   | Setting | Value |
   |---|---|
   | App name | `energy-waste-dashboard` |
   | Framework | Next.js |
   | Frontend build command | `npm run build` |
   | Build output directory | `.next` |
   | Service role | Create and use a new service role |
   | Build image | Amazon Linux 2023 |

![App settings](/images/5-Workshop/5.16/pic5.png)

5. **Add environment variables (Advanced settings)**

   | Key | Value |
   |---|---|
   | `NEXT_PUBLIC_AWS_REGION` | `ap-southeast-1` |
   | `NEXT_PUBLIC_COGNITO_USER_POOL_ID` | `ap-southeast-1_OiGmvapoL` |
   | `NEXT_PUBLIC_COGNITO_CLIENT_ID` | `42bod21u3a1g499u643mt056fm` |
   | `NEXT_PUBLIC_API_BASE_URL` | `https://51ioevkyjc.execute-api.ap-southeast-1.amazonaws.com` |

![Advanced settings and environment variables](/images/5-Workshop/5.16/pic6.png)

6. **Review and deploy**
   * Click **Next**, review the configuration, then click **Save and deploy**.

![Review](/images/5-Workshop/5.16/pic7.png)

Once the build finishes, the app appears on the Overview page with the deployed branch and domain URL.

![App overview after deployment](/images/5-Workshop/5.16/pic8.png)
