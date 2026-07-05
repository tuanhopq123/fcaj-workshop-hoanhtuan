---
title : "Create Daily Schedule at 00:05"
date : 2024-01-01
weight : 9
chapter : false
pre : " <b> 5.15.9. </b> "
---

EventBridge Scheduler will invoke the Lambda function daily at `00:05` in the `Asia/Ho_Chi_Minh` timezone. Since the Lambda function does not receive a `reportDate` from the Scheduler, it will automatically generate a report for the previous day.

#### Step 1: Open EventBridge Scheduler

1. Navigate to **Amazon EventBridge**.
2. In the left menu, select **Scheduler** -> **Schedules**.
3. Click **Create schedule**.

![Open EventBridge Scheduler](/images/5-Workshop/5.15-lambda-report/5.15.9-step1.png)

#### Step 2: Enter Schedule Details

1. For **Schedule name**, enter: `schedule_report_daily_0005`
2. For **Schedule group**, keep: `default`
3. Select **Recurring schedule**.
4. Select **Cron-based schedule**.
5. For **Cron expression**, enter: `cron(5 0 * * ? *)`
6. For **Timezone**, select: `Asia/Ho_Chi_Minh`
7. For **Flexible time window**, select: `Off`
8. Click **Next**.

![Schedule Details](/images/5-Workshop/5.15-lambda-report/5.15.9-step2.png)

#### Step 3: Select Target

1. Under Target detail, select **Templated target**.
2. Choose **AWS Lambda Invoke**.
3. For **Lambda function**, select: `energy-report-generator`
4. For **Payload**, paste the following JSON:

{
  "source": "eventbridge-scheduler"
}

*Note: Do not pass `reportDate`. The Lambda function will automatically retrieve the previous day's date according to UTC+7.*

5. Click **Next**.

![Select Target](/images/5-Workshop/5.15-lambda-report/5.15.9-step3.png)

#### Step 4: Configure Settings

1. For **Schedule state**, select: `Enable`
2. For **Action after schedule completion**, select: `None`
3. For **Retry policy**, select: `Off`
4. For **Dead-letter queue**, select: `None`
5. For **Encryption**, keep: `AWS owned key`
6. Under Permissions, select **Create new role for this schedule**.
7. For **Role name**, enter: `eventbridge-scheduler-energy-report-generator-role`
   *(AWS will automatically create a role granting the `lambda:InvokeFunction` permission for the `energy-report-generator` Lambda).*

![Configure Settings](/images/5-Workshop/5.15-lambda-report/5.15.9-step4.png)

#### Step 5: Review and Create Schedule

Verify the configuration summary:
- **Name**: `schedule_report_daily_0005`
- **Cron**: `cron(5 0 * * ? *)`
- **Timezone**: `Asia/Ho_Chi_Minh`
- **Target**: `energy-report-generator`
- **Payload**: `{"source": "eventbridge-scheduler"}`
- **Flexible time window**: `Off`
- **Schedule state**: `Enable`

Click **Create schedule** and wait for the success notification.

![Review and Create](/images/5-Workshop/5.15-lambda-report/5.15.9-step5.png)