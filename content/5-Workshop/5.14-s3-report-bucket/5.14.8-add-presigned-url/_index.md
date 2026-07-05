---
title : "Add Pre-signed URL to API Handler"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.14.8. </b> "
---

In Section 3, the `GET /reports/{date}` route only returned metadata from DynamoDB. Now, we will add the logic to generate a pre-signed URL. A pre-signed URL uses the permissions of the IAM principal that created the URL, which means the `energy-api-handler` role must have the permission to read the respective object.

#### Step 1: Open Source Code

1. Navigate back to **Lambda** -> **energy-api-handler** -> **Code** tab.
2. Open the `lambda_function.py` file.

#### Step 2: Add Bucket Configuration

Find the following line:
```python
REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")
Add the following lines immediately below it:

Python


REPORT_BUCKET = os.environ["REPORT_BUCKET"]
PRESIGNED_URL_EXPIRES_SECONDS = 900
The resulting block should look like this:

Python


DDB_TABLE = os.environ["DDB_TABLE"]
DEFAULT_ROOM_ID = os.environ.get("DEFAULT_ROOM_ID", "lab-01")
REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")
REPORT_BUCKET = os.environ["REPORT_BUCKET"]
PRESIGNED_URL_EXPIRES_SECONDS = 900
(Note: 900 seconds equals 15 minutes).

Step 3: Initialize S3 Client
Find the following lines:

Python


dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
Add the S3 client below them:

Python


s3_client = boto3.client("s3")
The resulting block should look like this:

Python


dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
s3_client = boto3.client("s3")
Step 4: Replace GET /reports/{date} Handler
Find the entire block handling if route_key == "GET /reports/{date}": and replace it with the following code:

Python


        if route_key == "GET /reports/{date}":
            report_date = path_parameters.get("date")

            if not report_date:
                return api_response(
                    400,
                    {
                        "success": False,
                        "message": "Thiếu tham số date."
                    }
                )

            if not re.fullmatch(r"\d{4}-\d{2}-\d{2}", report_date):
                return api_response(
                    400,
                    {
                        "success": False,
                        "message": "Ngày phải có định dạng YYYY-MM-DD."
                    }
                )

            report = get_report_by_date(report_date)

            if not report:
                return api_response(
                    404,
                    {
                        "success": False,
                        "date": report_date,
                        "message": "Chưa có báo cáo cho ngày này."
                    }
                )

            object_key = report.get("objectKey")
            report_bucket = report.get("bucket") or REPORT_BUCKET

            if not object_key:
                return api_response(
                    500,
                    {
                        "success": False,
                        "date": report_date,
                        "message": "Metadata báo cáo chưa có objectKey."
                    }
                )

            download_url = s3_client.generate_presigned_url(
                ClientMethod="get_object",
                Params={
                    "Bucket": report_bucket,
                    "Key": object_key
                },
                ExpiresIn=PRESIGNED_URL_EXPIRES_SECONDS
            )

            print(
                "Generated report pre-signed URL:",
                json.dumps(
                    {
                        "date": report_date,
                        "bucket": report_bucket,
                        "objectKey": object_key,
                        "expiresIn": PRESIGNED_URL_EXPIRES_SECONDS
                    },
                    ensure_ascii=False
                )
            )

            return api_response(
                200,
                {
                    "success": True,
                    "item": report,
                    "downloadUrl": download_url,
                    "expiresIn": PRESIGNED_URL_EXPIRES_SECONDS
                }
            )
```
Note: Boto3 provides generate_presigned_url to create a time-limited URL for an S3 operation, which in this case is get_object.

#### Step 5: Deploy
1. Click Deploy.

2. Wait for the notification: Successfully updated the function energy-api-handler.