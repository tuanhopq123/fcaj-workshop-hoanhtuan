---
title : "Test Lambda Directly"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.13.6. </b> "
---

We will test the Lambda function independently to verify its routing and database interactions before connecting it to Amazon API Gateway.

#### Test 1 — GET /rooms

1. Select the **Test** tab in your Lambda function.
2. Click **Create new event**.
3. For **Event name**, enter: `test_get_rooms`
4. Paste the following JSON payload:

{
  "version": "2.0",
  "routeKey": "GET /rooms",
  "rawPath": "/rooms",
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/rooms"
    }
  }
}

5. Click **Save** and then click **Test**.

**Expected Result:**
- `statusCode` = `200`
- `success` = `true`
- The `body` must contain room profile items with attributes similar to: `PK = ROOM#lab-01`, `SK = PROFILE`.
*(Note: The body is returned as a JSON string with escaped quotes `\"`; this is standard behavior for a Lambda proxy integration response).*

#### Test 2 — GET /telemetry

1. Create a new test event named: `test_get_telemetry`
2. Paste the following JSON payload:

{
  "version": "2.0",
  "routeKey": "GET /telemetry",
  "rawPath": "/telemetry",
  "queryStringParameters": {
    "roomId": "lab-01",
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/telemetry"
    }
  }
}

3. Click **Test**.

**Expected Result:**
- `statusCode` = `200`
- `roomId` = `lab-01`
- `count` > `0`
- The `items` array must include items with sort keys starting with: `TELEMETRY#`
*(Note: DynamoDB stores items with the same partition key ordered by their sort key. The function uses `ScanIndexForward=False` to fetch the latest records first).*

#### Test 3 — GET /alerts

1. Create a new test event named: `test_get_alerts`
2. Paste the following JSON payload:

{
  "version": "2.0",
  "routeKey": "GET /alerts",
  "rawPath": "/alerts",
  "queryStringParameters": {
    "roomId": "lab-01",
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/alerts"
    }
  }
}

3. Click **Test**.

**Expected Result:**
- `statusCode` = `200`
- `roomId` = `lab-01`
- The `items` array must include items with sort keys starting with: `ALERT#`

#### Test 4 — GET /reports

1. Create a new test event named: `test_get_reports`
2. Paste the following JSON payload:

{
  "version": "2.0",
  "routeKey": "GET /reports",
  "rawPath": "/reports",
  "queryStringParameters": {
    "limit": "20"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/reports"
    }
  }
}

3. Click **Test**.

**Expected Result at this stage:**
- `statusCode` = `200`
- `count` = `0`
- `message` = `Chưa có báo cáo.`
*(Note: This is expected and not an error because the Report Generator function has not been created yet).*

#### Test 5 — GET /reports/{date}

1. Create a new test event named: `test_get_report_by_date`
2. Paste the following JSON payload:

{
  "version": "2.0",
  "routeKey": "GET /reports/{date}",
  "rawPath": "/reports/2026-07-03",
  "pathParameters": {
    "date": "2026-07-03"
  },
  "requestContext": {
    "http": {
      "method": "GET",
      "path": "/reports/2026-07-03"
    }
  }
}

3. Click **Test**.

**Expected Result at this stage:**
- `statusCode` = `404`
- `message` = `Chưa có báo cáo cho ngày này.`
*(Note: This is also the correct expected output for the current phase).*

![Test Lambda Directly](/images/5-Workshop/5.13-lambda-api-handler/5.13.6-test-lambda.png)