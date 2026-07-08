---
title : "Disable Public Sign-Up"
date : 2026-07-05
weight : 5
chapter : false
pre : " <b> 5.11.5 </b> "
---

The lab monitoring dashboard should only be available to provisioned accounts. Therefore, we will create users manually as an admin instead of allowing public registration.

1. In the user pool menu, choose: **Sign-up**.
2. Find the section: **Self-service sign-up**.
3. Click: **Edit**.
4. Turn off / uncheck: **Enable self-registration**.
5. Click: **Save changes**.

When self-registration is disabled, users cannot sign up on their own; accounts must be created by an administrator in the Cognito Console or via the API.

![Disable Sign up](/images/5-Workshop/5.11-Cognito/Enable-self-registration.png)