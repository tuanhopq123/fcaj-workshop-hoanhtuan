---
title : "Create the JWT Fetch and API Gateway Call Function"
date : 2026-07-05
weight : 6
chapter : false
pre : " <b> 5.16.6 </b> "
---

Create the file:

```
src/lib/api.ts
```

Paste:

```ts
import { fetchAuthSession } from "aws-amplify/auth";

const rawApiBaseUrl =
  process.env.NEXT_PUBLIC_API_BASE_URL;

if (!rawApiBaseUrl) {
  throw new Error(
    "Missing NEXT_PUBLIC_API_BASE_URL."
  );
}

const API_BASE_URL = rawApiBaseUrl.replace(
  /\/+$/,
  ""
);

type ApiErrorBody = {
  message?: string;
  error?: string;
};

async function getJwtToken(): Promise<string> {
  let session = await fetchAuthSession();

  let token =
    session.tokens?.idToken?.toString() ??
    session.tokens?.accessToken?.toString();

  if (!token) {
    session = await fetchAuthSession({
      forceRefresh: true,
    });

    token =
      session.tokens?.idToken?.toString() ??
      session.tokens?.accessToken?.toString();
  }

  if (!token) {
    throw new Error(
      "The session has no JWT. " +
        "Please sign out and sign in again."
    );
  }

  return token;
}

export async function apiGet<T>(
  path: string
): Promise<T> {
  const jwtToken = await getJwtToken();

  const response = await fetch(
    `${API_BASE_URL}${path}`,
    {
      method: "GET",
      headers: {
        Authorization: `Bearer ${jwtToken}`,
        Accept: "application/json",
      },
      cache: "no-store",
    }
  );

  const responseText = await response.text();

  let responseBody: unknown = {};

  if (responseText) {
    try {
      responseBody = JSON.parse(responseText);
    } catch {
      responseBody = {
        message: responseText,
      };
    }
  }

  if (!response.ok) {
    const errorBody =
      responseBody as ApiErrorBody;

    throw new Error(
      errorBody.message ||
        errorBody.error ||
        `API returned error ${response.status}.`
    );
  }

  return responseBody as T;
}
```
