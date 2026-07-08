---
title : "Tạo trang đăng nhập và kiểm tra phiên Cognito"
date : 2026-07-05
weight : 8
chapter : false
pre : " <b> 5.16.8 </b> "
---

Mở:

```
src/app/page.tsx
```

Dán phiên bản cuối cùng:

```tsx
"use client";

import { useEffect, useState, type FormEvent } from "react";

import {
  fetchAuthSession,
  getCurrentUser,
  signIn,
  signOut,
} from "aws-amplify/auth";

import Dashboard from "@/components/Dashboard";

type SignedInUser = {
  username: string;
  userId: string;
  email: string;
};

async function loadValidUser(): Promise<SignedInUser> {
  const session = await fetchAuthSession();

  const idToken = session.tokens?.idToken?.toString();
  const accessToken = session.tokens?.accessToken?.toString();

  if (!idToken && !accessToken) {
    throw new Error("SESSION_HAS_NO_TOKEN");
  }

  const currentUser = await getCurrentUser();

  const emailClaim = session.tokens?.idToken?.payload.email;

  return {
    username: currentUser.username,
    userId: currentUser.userId,
    email: typeof emailClaim === "string" ? emailClaim : currentUser.username,
  };
}

async function clearInvalidSession(): Promise<void> {
  try {
    await signOut();
  } catch {
    // Bỏ qua lỗi để luôn quay về form đăng nhập.
  }
}

export default function Home() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");
  const [user, setUser] = useState<SignedInUser | null>(null);
  const [checkingSession, setCheckingSession] = useState(true);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  useEffect(() => {
    async function checkSession() {
      try {
        const currentUser = await loadValidUser();
        setUser(currentUser);
      } catch {
        await clearInvalidSession();
        setUser(null);
      } finally {
        setCheckingSession(false);
      }
    }

    void checkSession();
  }, []);

  async function handleSubmit(event: FormEvent<HTMLFormElement>) {
    event.preventDefault();

    setLoading(true);
    setError("");

    try {
      await clearInvalidSession();

      const result = await signIn({
        username: email.trim().toLowerCase(),
        password,
        options: {
          authFlowType: "USER_AUTH",
          preferredChallenge: "PASSWORD",
        },
      });

      if (!result.isSignedIn || result.nextStep.signInStep !== "DONE") {
        throw new Error(
          `Cognito yêu cầu bước tiếp theo: ${result.nextStep.signInStep}`
        );
      }

      const currentUser = await loadValidUser();

      setUser(currentUser);
      setPassword("");
    } catch (requestError) {
      await clearInvalidSession();
      setUser(null);

      setError(
        requestError instanceof Error
          ? requestError.message
          : "Không thể đăng nhập."
      );
    } finally {
      setLoading(false);
    }
  }

  async function handleSignOut() {
    setUser(null);
    setEmail("");
    setPassword("");
    setError("");

    try {
      await signOut();
    } catch {
      // Giao diện vẫn quay về form đăng nhập.
    }
  }

  if (checkingSession) {
    return (
      <main className="flex min-h-screen items-center justify-center bg-slate-100">
        <p className="text-slate-600">Đang kiểm tra phiên đăng nhập...</p>
      </main>
    );
  }

  if (user) {
    return <Dashboard email={user.email} onSignOut={handleSignOut} />;
  }

  return (
    <main className="flex min-h-screen items-center justify-center bg-slate-100 p-6">
      <form
        onSubmit={handleSubmit}
        className="w-full max-w-sm rounded-2xl bg-white p-7 shadow-lg"
      >
        <p className="text-sm font-semibold uppercase tracking-wider text-emerald-600">
          AWS Serverless Project
        </p>

        <h1 className="mt-2 text-2xl font-bold text-slate-900">Đăng nhập</h1>

        <p className="mt-2 text-sm text-slate-500">
          Smart Home Energy Waste Monitoring
        </p>

        <label htmlFor="email" className="mt-6 block text-sm font-medium text-slate-700">
          Email
        </label>

        <input
          id="email"
          type="email"
          autoComplete="username"
          value={email}
          onChange={(event) => setEmail(event.target.value)}
          required
          className="mt-2 w-full rounded-lg border border-slate-300 px-4 py-2 outline-none focus:border-emerald-600"
        />

        <label htmlFor="password" className="mt-4 block text-sm font-medium text-slate-700">
          Password
        </label>

        <input
          id="password"
          type="password"
          autoComplete="current-password"
          value={password}
          onChange={(event) => setPassword(event.target.value)}
          required
          className="mt-2 w-full rounded-lg border border-slate-300 px-4 py-2 outline-none focus:border-emerald-600"
        />

        {error && (
          <div className="mt-4 rounded-lg border border-red-200 bg-red-50 p-3 text-sm text-red-700">
            {error}
          </div>
        )}

        <button
          type="submit"
          disabled={loading}
          className="mt-5 w-full rounded-lg bg-emerald-700 px-4 py-2 font-semibold text-white hover:bg-emerald-600 disabled:cursor-not-allowed disabled:opacity-60"
        >
          {loading ? "Đang đăng nhập..." : "Sign in"}
        </button>
      </form>
    </main>
  );
}
```

![Trang đăng nhập đã deploy](/images/5-Workshop/5.16/pic10.png)
