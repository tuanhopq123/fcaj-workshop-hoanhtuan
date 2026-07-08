---
title : "Define your application"
date : 2026-07-05
weight : 2
chapter : false
pre : " <b> 5.11.2 </b> "
---

1. **Application type**
   * For Application type, choose: **Single-page application (SPA)**.
   * Do not choose: *Traditional web application, Machine-to-machine application, Mobile application*. 
   * *(A Next.js/React dashboard running in a browser is a public client, so the app client should not contain a client secret)*.

2. **Name your application**
   * For Application name, enter: `energy-waste-dashboard-client`.

3. **Sign-in identifiers**
   * For Options for sign-in identifiers, only choose: **Email**.
   * Uncheck Username or Phone number if selected. Users will log in with email and password.

4. **Required attributes for sign-up**
   * For Required attributes for sign-up, choose: **Email**.

5. **Add a return URL**
   * For Return URL, enter: `http://localhost:3000/`. 
   * *(This URL is used during the dashboard development phase on a local machine)*.

6. Check the configuration again and click: **Create your application**.
7. After the Setup page appears, scroll down and click: **Go to overview**.

![Define App](/images/5-Workshop/5.11-Cognito/01-cognito-application-settings.png)