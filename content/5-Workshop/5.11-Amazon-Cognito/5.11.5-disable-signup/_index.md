---
title : "Disable Public Sign-Up"
date : 2026-07-05
weight : 5
chapter : false
pre : " <b> 5.11.5 </b> "
---

The lab monitoring dashboard should only be available to provisioned accounts[cite: 14]. Therefore, we will create users manually as an admin instead of allowing public registration[cite: 14].

1. In the user pool menu, choose: **Sign-up**[cite: 14].
2. Find the section: **Self-service sign-up**[cite: 14].
3. Click: **Edit**[cite: 14].
4. Turn off / uncheck: **Enable self-registration**[cite: 14].
5. Click: **Save changes**[cite: 14].

When self-registration is disabled, users cannot sign up on their own; accounts must be created by an administrator in the Cognito Console or via the API[cite: 14].

![Disable Sign up](/images/5-Workshop/5.11-Cognito/Enable-self-registration.png)