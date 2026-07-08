---
title : "Tạo giao diện Dashboard"
date : 2026-07-05
weight : 7
chapter : false
pre : " <b> 5.16.7 </b> "
---

Tạo file:

```
src/components/Dashboard.tsx
```

Dán mã sau:

```tsx
"use client";

import { useCallback, useEffect, useState } from "react";

import { apiGet } from "@/lib/api";

type DataItem = Record<string, unknown>;

type ListResponse = {
  success?: boolean;
  count?: number;
  roomId?: string;
  items?: DataItem[];
  message?: string;
};

type ReportDetailResponse = {
  success?: boolean;
  item?: DataItem;
  downloadUrl?: string;
  expiresIn?: number;
  message?: string;
};

type DashboardProps = {
  email: string;
  onSignOut: () => Promise<void>;
};

function displayValue(value: unknown, fallback = "-"): string {
  if (value === null || value === undefined || value === "") {
    return fallback;
  }
  if (typeof value === "boolean") {
    return value ? "Có" : "Không";
  }
  return String(value);
}

function getRoomId(item: DataItem): string {
  if (typeof item.roomId === "string") return item.roomId;
  if (typeof item.PK === "string" && item.PK.startsWith("ROOM#")) {
    return item.PK.replace("ROOM#", "");
  }
  return "lab-01";
}

function getReportDate(item: DataItem): string {
  if (typeof item.date === "string") return item.date;
  if (typeof item.SK === "string" && item.SK.startsWith("REPORT#")) {
    return item.SK.replace("REPORT#", "");
  }
  return "";
}

function SummaryCard({
  title,
  value,
  description,
}: {
  title: string;
  value: number | string;
  description: string;
}) {
  return (
    <div className="rounded-2xl border border-slate-200 bg-white p-5 shadow-sm">
      <p className="text-sm font-medium text-slate-500">{title}</p>
      <p className="mt-2 text-3xl font-bold text-slate-900">{value}</p>
      <p className="mt-2 text-sm text-slate-500">{description}</p>
    </div>
  );
}

export default function Dashboard({ email, onSignOut }: DashboardProps) {
  const [selectedRoom, setSelectedRoom] = useState("lab-01");
  const [rooms, setRooms] = useState<DataItem[]>([]);
  const [telemetry, setTelemetry] = useState<DataItem[]>([]);
  const [alerts, setAlerts] = useState<DataItem[]>([]);
  const [reports, setReports] = useState<DataItem[]>([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState("");
  const [downloadingDate, setDownloadingDate] = useState("");

  const loadDashboard = useCallback(async () => {
    setLoading(true);
    setError("");

    try {
      const [roomsResult, telemetryResult, alertsResult, reportsResult] =
        await Promise.all([
          apiGet<ListResponse>("/rooms"),
          apiGet<ListResponse>(
            `/telemetry?roomId=${encodeURIComponent(selectedRoom)}&limit=20`
          ),
          apiGet<ListResponse>(
            `/alerts?roomId=${encodeURIComponent(selectedRoom)}&limit=20`
          ),
          apiGet<ListResponse>("/reports"),
        ]);

      const roomItems = roomsResult.items ?? [];

      setRooms(roomItems);
      setTelemetry(telemetryResult.items ?? []);
      setAlerts(alertsResult.items ?? []);
      setReports(reportsResult.items ?? []);

      if (
        roomItems.length > 0 &&
        !roomItems.some((room) => getRoomId(room) === selectedRoom)
      ) {
        setSelectedRoom(getRoomId(roomItems[0]));
      }
    } catch (requestError) {
      setError(
        requestError instanceof Error
          ? requestError.message
          : "Không thể tải dữ liệu Dashboard."
      );
    } finally {
      setLoading(false);
    }
  }, [selectedRoom]);

  useEffect(() => {
    void loadDashboard();
  }, [loadDashboard]);

  async function downloadReport(report: DataItem) {
    const reportDate = getReportDate(report);

    if (!reportDate) {
      setError("Metadata báo cáo không có ngày hợp lệ.");
      return;
    }

    setDownloadingDate(reportDate);
    setError("");

    const downloadTab = window.open("about:blank", "_blank");
    if (downloadTab) downloadTab.opener = null;

    try {
      const result = await apiGet<ReportDetailResponse>(
        `/reports/${encodeURIComponent(reportDate)}`
      );

      if (!result.downloadUrl) {
        throw new Error(result.message || "API không trả về downloadUrl.");
      }

      if (downloadTab) {
        downloadTab.location.href = result.downloadUrl;
      } else {
        window.location.href = result.downloadUrl;
      }
    } catch (requestError) {
      downloadTab?.close();
      setError(
        requestError instanceof Error
          ? requestError.message
          : "Không thể tải báo cáo."
      );
    } finally {
      setDownloadingDate("");
    }
  }

  return (
    <div className="min-h-screen bg-slate-100">
      <header className="border-b border-slate-800 bg-slate-950 text-white">
        <div className="mx-auto flex max-w-7xl items-center justify-between px-6 py-5">
          <div>
            <p className="text-xs font-semibold uppercase tracking-[0.2em] text-emerald-400">
              AWS Serverless Project
            </p>
            <h1 className="mt-1 text-xl font-bold">
              Smart Home Energy Waste Monitoring
            </h1>
          </div>

          <div className="flex items-center gap-4">
            <div className="hidden text-right sm:block">
              <p className="text-sm font-medium">{email}</p>
              <p className="text-xs text-slate-400">Cognito authenticated</p>
            </div>

            <button
              type="button"
              onClick={() => void onSignOut()}
              className="rounded-lg border border-slate-600 px-4 py-2 text-sm font-medium hover:bg-slate-800"
            >
              Đăng xuất
            </button>
          </div>
        </div>
      </header>

      <main className="mx-auto max-w-7xl space-y-8 px-6 py-8">
        <section className="flex flex-col justify-between gap-4 rounded-2xl bg-emerald-700 p-6 text-white shadow-lg md:flex-row md:items-center">
          <div>
            <h2 className="text-2xl font-bold">Energy Monitoring Dashboard</h2>
            <p className="mt-2 text-sm text-emerald-50">
              Theo dõi điện năng, cảnh báo lãng phí và báo cáo hằng ngày.
            </p>
          </div>

          <div className="flex flex-wrap items-center gap-3">
            <label htmlFor="room" className="text-sm font-medium">
              Phòng:
            </label>

            <select
              id="room"
              value={selectedRoom}
              onChange={(event) => setSelectedRoom(event.target.value)}
              className="rounded-lg bg-white px-4 py-2 text-sm text-slate-900"
            >
              {rooms.length === 0 && <option value="lab-01">lab-01</option>}

              {rooms.map((room, index) => {
                const roomId = getRoomId(room);
                return (
                  <option key={`${roomId}-${index}`} value={roomId}>
                    {displayValue(room.roomName ?? room.name ?? roomId)}
                  </option>
                );
              })}
            </select>

            <button
              type="button"
              onClick={() => void loadDashboard()}
              className="rounded-lg bg-white px-4 py-2 text-sm font-semibold text-emerald-700"
            >
              Làm mới
            </button>
          </div>
        </section>

        {error && (
          <div className="rounded-xl border border-red-200 bg-red-50 p-4 text-sm text-red-700">
            {error}
          </div>
        )}

        <section className="grid gap-4 md:grid-cols-2 xl:grid-cols-4">
          <SummaryCard title="Rooms" value={rooms.length} description="Phòng đã cấu hình" />
          <SummaryCard title="Telemetry" value={telemetry.length} description="20 mẫu gần nhất" />
          <SummaryCard title="Alerts" value={alerts.length} description="Cảnh báo gần nhất" />
          <SummaryCard title="Reports" value={reports.length} description="Báo cáo đã tạo" />
        </section>

        {loading ? (
          <div className="rounded-2xl bg-white p-10 text-center text-slate-500 shadow-sm">
            Đang tải dữ liệu từ API Gateway...
          </div>
        ) : (
          <>
            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">Telemetry gần nhất</h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">Thời gian</th>
                      <th className="px-6 py-3">Thiết bị</th>
                      <th className="px-6 py-3">Công suất</th>
                      <th className="px-6 py-3">Trạng thái</th>
                      <th className="px-6 py-3">Có người</th>
                      <th className="px-6 py-3">Lãng phí</th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {telemetry.map((item, index) => (
                      <tr key={displayValue(item.SK, String(index))}>
                        <td className="whitespace-nowrap px-6 py-3">
                          {displayValue(item.timestamp)}
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(item.deviceName ?? item.deviceId)}
                        </td>
                        <td className="px-6 py-3 font-medium">
                          {displayValue(item.powerW)} W
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(item.deviceStatus)}
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(item.occupancy)}
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(item.isWaste)}
                        </td>
                      </tr>
                    ))}

                    {telemetry.length === 0 && (
                      <tr>
                        <td colSpan={6} className="px-6 py-8 text-center text-slate-500">
                          Chưa có telemetry.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>

            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">Cảnh báo lãng phí</h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">Thời gian</th>
                      <th className="px-6 py-3">Thiết bị</th>
                      <th className="px-6 py-3">Công suất</th>
                      <th className="px-6 py-3">Nội dung</th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {alerts.map((item, index) => (
                      <tr key={displayValue(item.SK, String(index))}>
                        <td className="whitespace-nowrap px-6 py-3">
                          {displayValue(item.timestamp)}
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(item.deviceName ?? item.deviceId)}
                        </td>
                        <td className="px-6 py-3 font-medium text-red-600">
                          {displayValue(item.powerW)} W
                        </td>
                        <td className="px-6 py-3">
                          {displayValue(
                            item.message ?? item.reason ?? "Phát hiện lãng phí điện"
                          )}
                        </td>
                      </tr>
                    ))}

                    {alerts.length === 0 && (
                      <tr>
                        <td colSpan={4} className="px-6 py-8 text-center text-slate-500">
                          Chưa có cảnh báo.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>

            <section className="rounded-2xl bg-white shadow-sm">
              <div className="border-b border-slate-200 px-6 py-4">
                <h2 className="text-lg font-bold">Báo cáo điện năng</h2>
              </div>

              <div className="overflow-x-auto">
                <table className="min-w-full text-left text-sm">
                  <thead className="bg-slate-50 text-slate-600">
                    <tr>
                      <th className="px-6 py-3">Ngày</th>
                      <th className="px-6 py-3">Telemetry</th>
                      <th className="px-6 py-3">Alerts</th>
                      <th className="px-6 py-3">Điện năng</th>
                      <th className="px-6 py-3">Công suất TB</th>
                      <th className="px-6 py-3">Thao tác</th>
                    </tr>
                  </thead>

                  <tbody className="divide-y divide-slate-100">
                    {reports.map((item, index) => {
                      const reportDate = getReportDate(item);
                      return (
                        <tr key={reportDate || String(index)}>
                          <td className="px-6 py-3 font-medium">
                            {displayValue(reportDate)}
                          </td>
                          <td className="px-6 py-3">
                            {displayValue(item.telemetryCount)}
                          </td>
                          <td className="px-6 py-3">
                            {displayValue(item.alertCount)}
                          </td>
                          <td className="px-6 py-3">
                            {displayValue(item.totalEnergyKwh)} kWh
                          </td>
                          <td className="px-6 py-3">
                            {displayValue(item.averagePowerW)} W
                          </td>
                          <td className="px-6 py-3">
                            <button
                              type="button"
                              onClick={() => void downloadReport(item)}
                              disabled={downloadingDate === reportDate}
                              className="rounded-lg bg-slate-900 px-4 py-2 text-xs font-semibold text-white disabled:opacity-50"
                            >
                              {downloadingDate === reportDate
                                ? "Đang tạo URL..."
                                : "Tải JSON"}
                            </button>
                          </td>
                        </tr>
                      );
                    })}

                    {reports.length === 0 && (
                      <tr>
                        <td colSpan={6} className="px-6 py-8 text-center text-slate-500">
                          Chưa có báo cáo.
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </section>
          </>
        )}
      </main>
    </div>
  );
}
```

![Dashboard.tsx trong cấu trúc project](/images/5-Workshop/5.16/pic2.png)
