---
title : "Kiểm tra DynamoDB"
date : 2026-07-01
weight : 7
chapter : false
pre : " <b> 5.6.7 </b> "
---

1. **Mở Explore table items**
   * Vào `DynamoDB → Tables → EnergyWasteData → Explore table items`.

2. **Kiểm tra các item mới**
   * Bạn cần thấy có thêm item dạng:

```
TELEMETRY#2026-07-01T10:00:00Z#virtual-sensor-01
ALERT#2026-07-01T10:00:00Z#...
```

![Bảng EnergyWasteData - item Telemetry và Alert](/images/5-Workshop/5.6-lambda/pic11.png)
