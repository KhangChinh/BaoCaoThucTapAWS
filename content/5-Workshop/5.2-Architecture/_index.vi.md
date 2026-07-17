---
title : "Kiến trúc hệ thống"
date : 2026-07-17 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

# Phân tích và Thiết kế hệ thống kiến trúc

#### Sơ đồ kiến trúc tổng thể

Dự án được thiết kế theo mô hình Serverless trên nền tảng AWS, kết hợp với Frontend linh hoạt (ReactJS/Electron) để tối ưu hóa chi phí, đảm bảo hiệu năng và khả năng mở rộng tự động.

![Sơ đồ kiến trúc AWS](https://res.cloudinary.com/dqblg6ont/image/upload/v1784285383/uchimi-aws-architecture.drawio_mtvphq.png)

#### Các dịch vụ AWS cốt lõi

Dự án sử dụng bộ khung Serverless Framework để triển khai tự động cấu hình hạ tầng (Infrastructure as Code) với môi trường Node.js 20.x[cite: 4]. Cấu trúc tổng thể bao gồm 20 Lambda functions, 25 HTTP routes, 2 EventBridge schedules, 3 S3 triggers, 1 DynamoDB Stream trigger và 1 Cognito trigger[cite: 4].

Dưới đây là danh sách các dịch vụ đóng vai trò nền tảng trong kiến trúc:

| Dịch vụ | Mục đích sử dụng | Chi tiết cấu hình |
| :--- | :--- | :--- |
| **AWS Lambda** | Xử lý toàn bộ Business Logic | Phân chia thành các service độc lập: User, Session, Gacha, Minigame, Quest, Shop, Social, Upload, Currency, Sync[cite: 4]. |
| **API Gateway** | Cổng giao tiếp REST API cho Client | Quản lý 25 routes (POST/GET, PUT), cấu hình Throttling giới hạn 50 requests/s và 20 concurrent requests[cite: 4]. |
| **Amazon Cognito** | Xác thực và định danh người dùng | Sử dụng JWT Authorizer cho API Gateway, kết hợp Trigger PostConfirmation để tự động khởi tạo dữ liệu người dùng (`handleInitUser`)[cite: 4]. |
| **Amazon DynamoDB** | Lưu trữ Cơ sở dữ liệu NoSQL | Bao gồm 8 bảng chính: User, Study, Social, Quest, Minigame, ItemData, Inventory, GachaHistory[cite: 1, 4]. |
| **DynamoDB Streams** | Bắt sự kiện thay đổi dữ liệu thời gian thực | Kích hoạt Lambda `streamIndexer` trên User table để đồng bộ dữ liệu người dùng sang Algolia Search[cite: 4]. |
| **Amazon S3** | Lưu trữ tài nguyên tĩnh (Static Assets) | Quản lý bucket `ASSETS_BUCKET` chứa ảnh đại diện, file cấu hình trò chơi, và tự động kích hoạt Lambda xử lý khi có file `.zip` hoặc `.json` được upload[cite: 4]. |
| **Amazon EventBridge** | Lập lịch tác vụ tự động (Cron Jobs) | Kích hoạt worker cập nhật Bảng xếp hạng mỗi 10 phút và làm mới Cửa hàng hàng tuần vào 17:00 Chủ Nhật UTC (00:00 Thứ 2 giờ VN)[cite: 4]. |
| **Amazon CloudWatch** | Giám sát và Lưu trữ nhật ký (Logs) | Tự động tạo Log Group cho 20 hàm Lambda để ghi nhận lịch sử thực thi, hỗ trợ theo dõi hiệu năng và gỡ lỗi (debug) hệ thống[cite: 4]. |
| **AWS IAM** | Quản lý Định danh và Truy cập | Kiểm soát quyền truy cập của các hàm Lambda tới các tài nguyên AWS khác (S3, DynamoDB,...) thông qua các Role và Policy[cite: 4]. |
| **Amazon CloudFront** | Mạng phân phối nội dung (CDN) | Hoạt động ngầm để phân phối mượt mà các tài nguyên tĩnh (Avatars, Item assets) từ S3 đến người dùng cuối. |

#### Tích hợp dịch vụ bên thứ ba (Third-party)

Bên cạnh hệ sinh thái AWS, hệ thống tích hợp **Algolia** làm công cụ tìm kiếm Full-text search chuyên dụng. Dịch vụ này thay thế cho OpenSearch, đảm nhiệm việc truy vấn danh sách người dùng với tốc độ cao, được đồng bộ liên tục thông qua DynamoDB Streams[cite: 3].

#### Cấu hình bảo mật và Quyền truy cập (IAM Permissions)

Nguyên tắc đặc quyền tối thiểu (Least Privilege) được áp dụng nghiêm ngặt thông qua file `serverless.yml`[cite: 4]. Hệ thống chỉ cấp các quyền hành động (Actions) đích danh trên đúng các tài nguyên (Resources) cần thiết:

* **DynamoDB:** Cấp quyền `GetItem`, `PutItem`, `UpdateItem`, `DeleteItem`, `Query`, `Scan`, `BatchGetItem`, `BatchWriteItem`, `TransactWriteItems` trực tiếp lên 8 bảng hệ thống và các Global Secondary Indexes (GSI) tương ứng[cite: 4].
* **DynamoDB Streams:** Giới hạn quyền `DescribeStream`, `GetRecords`, `GetShardIterator`, và `ListStreams` duy nhất trên ARN của User Table Stream[cite: 4].
* **Amazon S3:** Chỉ cho phép `GetObject` và `PutObject` trong giới hạn các thư mục chỉ định như `public-assets/*`, `avatars/*`, và `uploads/*`[cite: 4].

```json
service: aws-uchimi
useDotenv: true
plugins:
  - serverless-api-gateway-throttling
custom:
  apiGatewayThrottling:
    maxRequestsPerSecond: 50
    maxConcurrentRequests: 20
build:
  esbuild:
    bundle: true
    minify: true
    external:
      - '@aws-sdk/*'
provider:
  name: aws
  runtime: nodejs20.x
  region: ${env:AWS_REGION}
  memorySize: 512
  environment:
    ALGOLIA_APP_ID: ${env:ALGOLIA_APP_ID}
    ALGOLIA_WRITE_KEY: ${env:ALGOLIA_WRITE_KEY}
    ALGOLIA_USER_INDEX: ${env:ALGOLIA_USER_INDEX}
    ASSETS_BUCKET: ${env:ASSETS_BUCKET}
    DEFAULT_AVATAR_URL: ${env:DEFAULT_AVATAR_URL}
    USER_TABLE: ${env:USER_TABLE}
    STUDY_TABLE: ${env:STUDY_TABLE}
    SOCIAL_TABLE: ${env:SOCIAL_TABLE}
    QUEST_TABLE: ${env:QUEST_TABLE}
    MINIGAME_TABLE: ${env:MINIGAME_TABLE}
    ITEMDATA_TABLE: ${env:ITEMDATA_TABLE}
    INVENTORY_TABLE: ${env:INVENTORY_TABLE}
    GACHAHISTORY_TABLE: ${env:GACHAHISTORY_TABLE}
    INVENTORY_TYPES: ${env:INVENTORY_TYPES}
    VERSION: ${env:VERSION}

  iam:
    role:
      statements:
        # ── DynamoDB ──────────────────────────────────────
        - Effect: Allow
          Action:
            - dynamodb:GetItem
            - dynamodb:PutItem
            - dynamodb:UpdateItem
            - dynamodb:DeleteItem
            - dynamodb:Query
            - dynamodb:Scan
            - dynamodb:BatchGetItem
            - dynamodb:BatchWriteItem
            - dynamodb:TransactWriteItems
          Resource:
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:USER_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:USER_TABLE}/index/*"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:STUDY_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:SOCIAL_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:QUEST_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:MINIGAME_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:MINIGAME_TABLE}/index/*"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:ITEMDATA_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:INVENTORY_TABLE}"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:INVENTORY_TABLE}/index/*"
            - "arn:aws:dynamodb:${self:provider.region}:*:table/${env:GACHAHISTORY_TABLE}"
        # ── DynamoDB Streams (streamIndexer Lambda) ───────
        - Effect: Allow
          Action:
            - dynamodb:DescribeStream
            - dynamodb:GetRecords
            - dynamodb:GetShardIterator
            - dynamodb:ListStreams
          Resource:
            - "${env:USER_TABLE_STREAM_ARN}"
        # ── S3 ────────────────────────────────────────────
        - Effect: Allow
          Action:
            - s3:GetObject
            - s3:PutObject
          Resource:
            - "arn:aws:s3:::${env:ASSETS_BUCKET}/public-assets/*"
            - "arn:aws:s3:::${env:ASSETS_BUCKET}/avatars/*"
            - "arn:aws:s3:::${env:ASSETS_BUCKET}/uploads/*"

  httpApi:
    cors: true
    authorizers:
      myCognitoAuth:
        type: jwt
        identitySource: $request.header.Authorization
        issuerUrl: https://cognito-idp.${self:provider.region}.amazonaws.com/${env:COGNITO_USER_POOL_ID}
        audience:
          - ${env:COGNITO_CLIENT_ID}

functions:
  - ${file(./src/uploadFunction/function.yml)}
  - ${file(./src/userFunction/function.yml)}
  - ${file(./src/sessionFunction/function.yml)}
  - ${file(./src/currencyFunction/function.yml)}
  - ${file(./src/gachaFunction/function.yml)}
  - ${file(./src/minigameFunction/function.yml)}
  - ${file(./src/questFunction/function.yml)}
  - ${file(./src/shopFunction/function.yml)}
  - ${file(./src/socialFunction/function.yml)}
  - ${file(./src/syncFunction/function.yml)}