---
title: "Worklog Tuần 7"
date: 2026-06-15
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu tuần 7:

* Phát triển tính năng tương tác xã hội cốt lõi: hệ thống kết bạn giữa các người dùng.
* Tự động hóa luồng làm mới (refresh) nhiệm vụ hàng ngày thông qua AWS Lambda trigger.
* Xây dựng công cụ tìm kiếm người dùng tốc độ cao bằng cách tích hợp AWS OpenSearch với DynamoDB.
* Chuẩn hóa việc quản lý hạ tầng (Infrastructure as Code) cho dự án Serverless Node.js bằng CloudFormation.
* Tối ưu hóa pipeline nhập liệu vật phẩm tự động từ AWS S3 vào DynamoDB.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Viết logic kết bạn giữa 2 người dùng (xử lý dữ liệu trên social table) | 15/06/2026 | 15/06/2026 | |
| 3 | - Viết logic chức năng tự động refresh nhiệm vụ ngày qua trigger Lambda | 16/06/2026 | 16/06/2026 | [AWS Lambda Triggers](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html) |
| 4 | - Ứng dụng AWS OpenSearch kết nối với DynamoDB để quản lý chức năng tìm kiếm người dùng | 17/06/2026 | 17/06/2026 | [Amazon OpenSearch Service](https://aws.amazon.com/opensearch-service/) |
| 5 | - Tìm hiểu và sử dụng CloudFormation cấu hình cho dự án serverless | 18/06/2026 | 18/06/2026 | [AWS CloudFormation](https://aws.amazon.com/cloudformation/) |
| 6 | - Viết event trigger cho S3 (assets bucket) để upload dữ liệu vật phẩm lên DynamoDB tự động | 19/06/2026 | 19/06/2026 | |


### Kết quả đạt được tuần 7:

* Hoàn thành API kết bạn, cho phép người dùng gửi yêu cầu và thiết lập mối quan hệ thành công.
* Chức năng làm mới quest hàng ngày hoạt động chính xác dựa trên lịch trình kích hoạt của Lambda, đảm bảo trải nghiệm liên tục cho người dùng.
* Cấu hình thành công OpenSearch endpoint đồng bộ dữ liệu từ user table của DynamoDB, mang lại khả năng tìm kiếm người dùng linh hoạt và nhanh chóng hơn.
* Chuyển đổi thành công việc khai báo tài nguyên (hàm Lambda, quyền truy cập, biến môi trường) sang template của CloudFormation, giúp việc deploy dự án trở nên tự động và dễ kiểm soát.
* Xây dựng thành công luồng S3 trigger: mỗi khi có file dữ liệu vật phẩm mới được đẩy lên bucket, Lambda sẽ tự động đọc và ghi thông tin vào DynamoDB mà không cần can thiệp thủ công.