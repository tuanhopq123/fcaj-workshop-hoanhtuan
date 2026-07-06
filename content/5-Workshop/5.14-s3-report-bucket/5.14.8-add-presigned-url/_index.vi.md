---
title : "Bổ sung pre-signed URL vào mã API Handler"
date : 2024-01-01
weight : 8
chapter : false
pre : " <b> 5.14.8. </b> "
---

Ở Hạng mục 3, route GET /reports/{date} mới chỉ trả về metadata lưu trong DynamoDB. Bây giờ chúng ta sẽ bổ sung logic tạo pre-signed URL. Pre-signed URL sử dụng quyền của IAM principal đã tạo ra URL đó, vì vậy role của energy-api-handler bắt buộc phải có quyền đọc object tương ứng trên S3.

Bước 1: Mở mã nguồn
Quay lại: Lambda -> energy-api-handler -> tab Code.

Mở file: lambda_function.py.

Bước 2: Thêm cấu hình bucket
Tìm đoạn:

```Python


REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")
Thêm 2 dòng sau ngay bên dưới:

Python


REPORT_BUCKET = os.environ["REPORT_BUCKET"]
PRESIGNED_URL_EXPIRES_SECONDS = 900
Kết quả sẽ trông như thế này:

Python


DDB_TABLE = os.environ["DDB_TABLE"]
DEFAULT_ROOM_ID = os.environ.get("DEFAULT_ROOM_ID", "lab-01")
REPORTS_PK = os.environ.get("REPORTS_PK", "REPORTS")
REPORT_BUCKET = os.environ["REPORT_BUCKET"]
PRESIGNED_URL_EXPIRES_SECONDS = 900
(Lưu ý: 900 giây tương đương 15 phút).

Bước 3: Khởi tạo S3 client
Tìm đoạn code khởi tạo DynamoDB:

Python


dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
Thêm dòng khởi tạo S3 client ngay bên dưới:

Python


s3_client = boto3.client("s3")
Kết quả:

Python


dynamodb = boto3.resource("dynamodb")
table = dynamodb.Table(DDB_TABLE)
s3_client = boto3.client("s3")
Bước 4: Thay phần xử lý GET /reports/{date}
Tìm toàn bộ khối mã xử lý if route_key == "GET /reports/{date}": và thay thế toàn bộ bằng đoạn code sau:

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
Lưu ý: Boto3 hỗ trợ hàm generate_presigned_url để tạo một URL có thời hạn cho một thao tác S3 cụ thể, trong trường hợp này là get_object.

#### Bước 5: Deploy mã nguồn
1. Bấm nút: Deploy.

2. Chờ hệ thống thông báo: Successfully updated the function energy-api-handler.