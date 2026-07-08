---
title: "5.4. Tạo bảng DynamoDB"
date: 2026-07-01T17:00:00+07:00
draft: false
weight: 4
tags: ["aws", "dynamodb", "database"]
categories: ["Workshop"]
description: "Tổng quan về việc tạo bảng DynamoDB để lưu hồ sơ phòng và dữ liệu lãng phí năng lượng cho dự án."
---

Amazon DynamoDB được dùng làm kho dữ liệu chính của dự án, lưu trữ hồ sơ phòng và dữ liệu lãng phí năng lượng thu thập từ cảm biến.

Trong phần này, chúng ta sẽ thực hiện 3 bước chính:

### 1. [Tạo bảng DynamoDB](5.4.1-create-dynamodb/)
Hướng dẫn cách truy cập console DynamoDB và bắt đầu tạo bảng `EnergyWasteData`.

### 2. [Cấu hình Table Details](5.4.2-configure-table/)
Hướng dẫn từng bước để cấu hình partition key, sort key và capacity mode cho bảng.

### 3. [Tạo item Room mẫu](5.4.3-create-sample-item/)
Cách tạo một item mẫu trong bảng để kiểm tra bảng hoạt động đúng.
