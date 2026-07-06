---
title : "Define your application"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.11.2 </b> "
---

1. **Application type**[cite: 14]
   * For Application type, choose: **Single-page application (SPA)**[cite: 14].
   * Do not choose: *Traditional web application, Machine-to-machine application, Mobile application*[cite: 14]. 
   * *(A Next.js/React dashboard running in a browser is a public client, so the app client should not contain a client secret)*[cite: 14].

2. **Name your application**[cite: 14]
   * For Application name, enter: `energy-waste-dashboard-client`[cite: 14].

3. **Sign-in identifiers**[cite: 14]
   * For Options for sign-in identifiers, only choose: **Email**[cite: 14].
   * Uncheck Username or Phone number if selected[cite: 14]. Users will log in with email and password[cite: 14].

4. **Required attributes for sign-up**[cite: 14]
   * For Required attributes for sign-up, choose: **Email**[cite: 14].

5. **Add a return URL**[cite: 14]
   * For Return URL, enter: `http://localhost:3000/`[cite: 14]. 
   * *(This URL is used during the dashboard development phase on a local machine)*[cite: 14].

6. Check the configuration again and click: **Create your application**[cite: 14].
7. After the Setup page appears, scroll down and click: **Go to overview**[cite: 14].

![Define App](/images/5-Workshop/5.11-Cognito/01-cognito-application-settings.png)