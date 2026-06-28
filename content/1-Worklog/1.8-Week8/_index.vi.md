---
title: "Worklog Tuần 8"
date: 2026-06-22
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Cấu hình và thiết lập hoàn thiện hạ tầng máy chủ cho hệ thống tìm kiếm AWS OpenSearch.
* Tự động hóa luồng đồng bộ dữ liệu người dùng mới lên hệ thống tìm kiếm (indexing) ngay khi đăng ký thành công.
* Theo dõi, đôn đốc và quản lý tiến độ làm việc của các thành viên trong nhóm.
* Thực hiện đánh giá chéo (cross-review) và kiểm thử (testing) các module do thành viên khác thực hiện để đảm bảo tính đồng nhất của hệ thống.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Set up server và cluster cho dịch vụ AWS OpenSearch | 22/06/2026 | 22/06/2026 | [Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/what-is.html) |
| 3 | - Viết hàm trigger đồng bộ dữ liệu lên server search khi người dùng tạo tài khoản | 23/06/2026 | 23/06/2026 | |
| 4 | - Quản lý tiến độ làm việc, hỗ trợ giải quyết khó khăn của các thành viên khác trong nhóm | 24/06/2026 | 24/06/2026 | |
| 5 | - Kiểm tra các chức năng được thực hiện bởi các thành viên khác để đảm bảo đúng luồng vận hành của dự án | 25/06/2026 | 25/06/2026 | |


### Kết quả đạt được tuần 8:

* Cấu hình thành công môi trường AWS OpenSearch, đảm bảo khả năng xử lý truy vấn văn bản tốc độ cao.
* Hàm trigger (Lambda) hoạt động ổn định: thông tin người dùng được tự động đẩy (index) lên OpenSearch ngay khi họ tạo tài khoản thành công mà không có độ trễ lớn.
* Nắm bắt và kiểm soát tốt tiến độ của toàn nhóm, đảm bảo các task được hoàn thành theo đúng timeline đã cam kết.
* Qua quá trình review và kiểm thử sát sao, các module do thành viên khác phát triển đã được tích hợp trơn tru, không gây xung đột và bám sát tuyệt đối vào luồng nghiệp vụ cốt lõi của dự án.