---
title : "Cấu hình Amplify kết nối Cognito"
date : 2026-07-05
weight : 4
chapter : false
pre : " <b> 5.16.4 </b> "
---

Tạo file:

```
src/components/ConfigureAmplifyClientSide.tsx
```

Dán mã nguồn cuối cùng:

```tsx
"use client";

import { Amplify } from "aws-amplify";

const userPoolId =
  process.env.NEXT_PUBLIC_COGNITO_USER_POOL_ID;

const userPoolClientId =
  process.env.NEXT_PUBLIC_COGNITO_CLIENT_ID;

if (!userPoolId || !userPoolClientId) {
  throw new Error(
    "Thiếu Cognito User Pool ID hoặc App Client ID."
  );
}

Amplify.configure({
  Auth: {
    Cognito: {
      userPoolId,
      userPoolClientId,
      loginWith: {
        email: true,
      },
    },
  },
});

export default function ConfigureAmplifyClientSide() {
  return null;
}
```
