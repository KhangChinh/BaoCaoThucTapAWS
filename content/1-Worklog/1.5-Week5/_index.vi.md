---
title: "Worklog Tuần 5"
date: 2026-06-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Tối ưu hóa cơ sở dữ liệu để đạt hiệu suất cao và giảm thiểu chi phí truy vấn.
* Chuyển dịch thành công các luồng logic cốt lõi (tạo tài khoản, khởi tạo DB) lên môi trường Serverless của AWS.
* Hoàn thiện các module chức năng quản lý phiên làm việc và vật phẩm trong ứng dụng.
* Nắm bắt cách lưu trữ và quản lý tệp tĩnh tĩnh (ảnh đại diện) một cách an toàn với AWS S3.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Điều chỉnh database thông qua DBeaver để tối ưu chi phí query | 01/06/2026 | 01/06/2026 | |
| 3 | - Chuyển logic tạo tài khoản lên AWS | 02/06/2026 | 02/06/2026 | |
| 4 | - Thiết lập tự động theo dõi tài khoản người dùng để khởi tạo DB | 03/06/2026 | 03/06/2026 | |
| 5 | - Viết logic quản lý phiên, quản lý vật phẩm trên VS Code với extension Windsurf | 04/06/2026 | 04/06/2026 | |
| 6 | - Tìm hiểu AWS S3 để quản lý ảnh đại diện | 05/06/2026 | 05/06/2026 | [AWS S3 Documentation](https://aws.amazon.com/s3/) |


### Kết quả đạt được tuần 5:

* Cơ sở dữ liệu được tinh chỉnh hợp lý, tối ưu hóa được các câu lệnh truy vấn và tiết kiệm chi phí hiệu quả.
* Luồng tạo tài khoản và tự động khởi tạo cơ sở dữ liệu riêng cho người dùng mới đã hoạt động trơn tru trên kiến trúc AWS.
* Hoàn tất việc lập trình các logic xử lý phiên đăng nhập và quản lý vật phẩm trong dự án.
* Hiểu rõ cơ chế của bucket trong AWS S3, các phương thức bảo mật tệp tin và chuẩn bị sẵn sàng cho tính năng tải lên ảnh đại diện của người dùng.