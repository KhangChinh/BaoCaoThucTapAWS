---
title: "Worklog Tuần 6"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:

* Chuẩn hóa và làm rõ toàn bộ quy trình luồng nghiệp vụ của hệ thống.
* Nâng cao tính bảo mật cho ứng dụng thông qua việc tối ưu hóa quản lý token đăng nhập.
* Nghiên cứu giải pháp tự động hóa tác vụ ngầm trên server sử dụng dịch vụ AWS EventBridge.
* Tách bạch và tối ưu hóa cấu trúc cơ sở dữ liệu (schema DB) để giảm thiểu số lượng API calls không cần thiết từ phía Client lên AWS.
* Thiết kế giải pháp quản lý phiên (session logic) tối ưu cho hai phân hệ cốt lõi: Học tập và Minigame.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Thiết kế và hoàn thiện tài liệu luồng tất cả nghiệp vụ của dự án | 08/06/2026 | 08/06/2026 | |
| 3 | - Xây dựng logic quản lý và lưu trữ token đăng nhập của người dùng | 09/06/2026 | 09/06/2026 | |
| 4 | - Tìm hiểu dịch vụ AWS EventBridge phục vụ quản lý các chức năng chạy ngầm trên server | 10/06/2026 | 10/06/2026 | [AWS EventBridge Documentation](https://aws.amazon.com/eventbridge/) |
| 5 | - Tinh chỉnh và điều chỉnh schema database nhằm giảm tải việc Client gọi API lên AWS | 11/06/2026 | 11/06/2026 | |
| 6 | - Nghiên cứu và thiết kế logic session cho mảng học tập & minigame của ứng dụng | 12/06/2026 | 12/06/2026 | |


### Kết quả đạt được tuần 6:

* Hoàn thành sơ đồ tổng thể và tài liệu hóa toàn bộ luồng nghiệp vụ của dự án, giúp định hướng triển khai rõ ràng cho các giai đoạn tiếp theo.
* Hệ thống xử lý token hoạt động an toàn, đảm bảo kiểm soát tốt quyền truy cập và duy trì trạng thái đăng nhập hợp lệ cho người dùng.
* Nắm vững cơ chế hoạt động của AWS EventBridge (Event Bus, Rules, Targets) và lên được phương án triển khai các tác vụ định kỳ (cron jobs) chạy ngầm trên kiến trúc Serverless.
* Schema database được cải tiến thành công nhờ kỹ thuật gom cụm dữ liệu hợp lý, giảm đáng kể tần suất gọi API từ Client, tiết kiệm tài nguyên và chi phí AWS.
* Hoàn thiện mô hình xử lý session cho mảng học tập và minigame, đảm bảo dữ liệu quá trình chơi/học của người dùng luôn được lưu trữ chính xác và tức thời.