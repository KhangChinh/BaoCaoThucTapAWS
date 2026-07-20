---
title: "Worklog Tuần 10"
date: 2026-07-06
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

* Hoàn tất phân hệ minigame, đảm bảo tính năng tạo màn chơi hoạt động trơn tru.
* Tự động hóa hệ thống cửa hàng (shop) bằng cron job trên AWS EventBridge.
* Đánh giá lại hạ tầng tìm kiếm, quyết định hủy AWS OpenSearch và chuyển đổi sang nền tảng Algolia để tối ưu hiệu năng.
* Thực hiện kiểm tra tổng quan toàn bộ hệ thống (End-to-End Testing) để đảm bảo chất lượng.
* Nghiên cứu mạng phân phối nội dung (CDN) AWS CloudFront để tăng tốc độ tải trang và bảo mật.
* Tài liệu hóa luồng hệ thống, làm tiền đề quan trọng cho việc thiết kế sơ đồ kiến trúc (Architecture Diagram).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Hỗ trợ team hoàn thiện chức năng tạo màn chơi (level generation) cho minigame | 06/07/2026 | 06/07/2026 | |
| 3 | - Dùng AWS EventBridge để tạo cron job reset shop bán hàng hàng tuần | 07/07/2026 | 07/07/2026 | [AWS EventBridge Scheduler](https://aws.amazon.com/eventbridge/scheduler/) |
| 4 | - Hủy dịch vụ AWS OpenSearch, thực hiện chuyển sang Algolia <br> - Tìm hiểu dịch vụ CloudFront để chuẩn bị tích hợp vào dự án | 08/07/2026 | 08/07/2026 | [Algolia](https://www.algolia.com/) <br> [Amazon CloudFront](https://aws.amazon.com/cloudfront/) |
| 5 | - Kiểm tra tổng quan toàn bộ các chức năng đã có trong dự án | 09/07/2026 | 09/07/2026 | |
| 6 | - Tổng hợp các luồng dữ liệu (data flow) vào file text hỗ trợ cho việc vẽ sơ đồ kiến trúc dự án | 10/07/2026 | 10/07/2026 | |


### Kết quả đạt được tuần 10:

* Chức năng tạo màn chơi cho minigame đã được hoàn thiện và tích hợp thành công vào luồng chính của ứng dụng.
* Thiết lập thành công lịch trình (cron job) trên EventBridge, giúp cửa hàng tự động làm mới danh sách vật phẩm mỗi tuần một cách chính xác.
* Chuyển đổi thành công hệ thống tìm kiếm sang Algolia, giúp đơn giản hóa quá trình vận hành và cải thiện tốc độ truy vấn so với OpenSearch.
* Nắm vững cơ chế caching và phân phối nội dung của CloudFront, chuẩn bị sẵn sàng cho việc tối ưu tốc độ tải tài nguyên tĩnh (ảnh, assets).
* Qua quá trình kiểm tra tổng quát (QA), hệ thống vận hành ổn định, các chức năng liên kết chặt chẽ và không phát hiện lỗi nghiêm trọng.
* Hoàn thành bản mô tả text chi tiết về luồng kiến trúc (API Gateway, Lambda, DynamoDB, S3...), tạo cơ sở vững chắc để vẽ sơ đồ Architecture chính thức cho báo cáo.