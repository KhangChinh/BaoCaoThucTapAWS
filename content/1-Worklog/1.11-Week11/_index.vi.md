---
title: "Worklog Tuần 11"
date: 2026-07-13
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

* Tối ưu hóa tốc độ tải tài nguyên tĩnh bằng cách định tuyến Client qua mạng phân phối nội dung (CDN) AWS CloudFront.
* Trực quan hóa toàn bộ hệ thống bằng sơ đồ kiến trúc (Architecture Diagram) chuẩn mực.
* Đóng gói (build) ứng dụng thành tệp thực thi (.exe) và triển khai lên môi trường Production.
* Thực hiện kiểm thử trực tiếp trên Production để đảm bảo sản phẩm vận hành hoàn hảo trước khi nghiệm thu.
* Chuẩn bị kịch bản demo và đề cương chi tiết cho báo cáo tổng kết dự án.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Thay đổi cấu hình để Client gọi đến AWS CloudFront thay vì gọi trực tiếp vào S3 | 13/07/2026 | 13/07/2026 | [Amazon CloudFront](https://aws.amazon.com/cloudfront/) |
| 3 | - Vẽ và hoàn thiện sơ đồ kiến trúc dự án | 14/07/2026 | 14/07/2026 | |
| 4 | - Nén/build dự án thành file .exe để deploy <br> - Tải và kiểm tra các chức năng trên môi trường production | 15/07/2026 | 15/07/2026 | |
| 5 | - Lên kịch bản và chuẩn bị nội dung để quay video demo cho dự án | 16/07/2026 | 16/07/2026 | |
| 6 | - Tổng hợp số liệu và chuẩn bị nội dung để viết báo cáo dự án | 17/07/2026 | 17/07/2026 | |


### Kết quả đạt được tuần 11:

* Đã cấu hình thành công CloudFront Distribution, giúp Client tải tệp tĩnh nhanh và bảo mật hơn rất nhiều so với truy cập trực tiếp S3.
* Sơ đồ kiến trúc hệ thống được vẽ chi tiết, thể hiện rõ ràng luồng tương tác giữa các dịch vụ AWS (API Gateway, Lambda, DynamoDB, Cognito, S3, CloudFront...).
* Dự án được đóng gói thành công dưới dạng file `.exe`. Quá trình deploy lên Production diễn ra suôn sẻ.
* Qua quá trình kiểm tra thực tế (User Acceptance Testing) trên Production, tất cả các tính năng cốt lõi đều hoạt động ổn định, không phát sinh lỗi.
* Đã hoàn thiện kịch bản chi tiết cho video demo và lập xong dàn ý đầy đủ cho tài liệu báo cáo cuối khóa.