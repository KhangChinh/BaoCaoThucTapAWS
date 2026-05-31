---
title: "Worklog Tuần 4"
date: 2026-05-25
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Hoàn thiện trải nghiệm người dùng với luồng xác thực (authentication) và phân quyền mượt mà, bảo mật.
* Nắm bắt kiến thức cốt lõi về kiến trúc Serverless trên AWS thông qua API Gateway và Lambda.
* Nghiên cứu tư duy bảo mật hiện đại với hệ thống zero-trust client.
* Lên kế hoạch và chuẩn bị các bước logic cần thiết để dịch chuyển backend lên môi trường AWS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Chỉnh lại phân quyền và xác thực <br> - Lưu token của người dùng và làm chức năng refresh đăng nhập mỗi khi mở app | 25/05/2026 | 25/05/2026 | |
| 3 | - Tìm hiểu dịch vụ AWS API Gateway và AWS Lambda | 26/05/2026 | 26/05/2026 | [AWS Lambda](https://aws.amazon.com/lambda/) <br> [API Gateway](https://aws.amazon.com/api-gateway/) |
| 4 | - Tìm hiểu thế nào là hệ thống zero-trust client | 27/05/2026 | 27/05/2026 | |
| 5 | - Liệt kê các logic để chuyển phần backend lên AWS | 28/05/2026 | 28/05/2026 | |


### Kết quả đạt được tuần 4:

* Hoàn thiện hệ thống xác thực: token của người dùng được lưu trữ an toàn và tính năng tự động làm mới (refresh) đăng nhập khi mở app hoạt động ổn định.
* Nắm được cơ chế hoạt động, lợi ích và cách ứng dụng của AWS API Gateway cùng AWS Lambda.
* Hiểu rõ triết lý thiết kế của hệ thống zero-trust client để áp dụng vào việc tăng cường bảo mật cho dự án.
* Lập được danh sách chi tiết các logic và luồng dữ liệu cần thiết làm tiền đề cho quá trình đưa backend lên AWS.