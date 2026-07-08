---
title : "Configure CSS and Layout"
date : 2026-07-05
weight : 5
chapter : false
pre : " <b> 5.16.5 </b> "
---

**File `src/app/globals.css`**

Replace the content with:

```css
@import "tailwindcss";

:root {
  color-scheme: light;
}

html {
  background: #f1f5f9;
}

body {
  min-height: 100vh;
  margin: 0;
  background: #f1f5f9;
  color: #0f172a;
  font-family: Arial, Helvetica, sans-serif;
}

button,
input,
select {
  font: inherit;
}
```

**File `src/app/layout.tsx`**

```tsx
import type { Metadata } from "next";
import type { ReactNode } from "react";

import "./globals.css";

import ConfigureAmplifyClientSide from "@/components/ConfigureAmplifyClientSide";

export const metadata: Metadata = {
  title: "Energy Waste Dashboard",
  description:
    "Smart Home Energy Waste Monitoring and Alert System",
};

export default function RootLayout({
  children,
}: Readonly<{
  children: ReactNode;
}>) {
  return (
    <html
      lang="vi"
      suppressHydrationWarning
    >
      <body>
        <ConfigureAmplifyClientSide />
        {children}
      </body>
    </html>
  );
}
```
