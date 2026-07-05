---
title: "Worklog Tuần 9"
date: 2026-06-29
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu tuần 9:

* Xử lý sự cố hạ tầng: giải quyết nhanh chóng tình trạng tài khoản AWS bị khóa để không làm gián đoạn dự án.
* Tối ưu hóa và bảo trì: Sửa lỗi (bug fixes) và nâng cấp các hàm logic cũ, đồng thời cập nhật lại model cho AWS OpenSearch.
* Phát triển tính năng cốt lõi: Thiết kế và hoàn thiện toàn bộ luồng logic cho hệ thống quay thưởng (Gacha) và quy đổi tiền tệ trong ứng dụng.
* Hỗ trợ chéo trong nhóm: Hỗ trợ thành viên khác xây dựng chức năng tạo màn chơi cho phân hệ minigame.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm việc với support/ticket để giải quyết tình trạng bị AWS khóa tài khoản <br> - Sửa lỗi và bổ sung chức năng cho các hàm cũ | 29/06/2026 | 29/06/2026 | |
| 3 | - Chỉnh sửa và tối ưu hóa model của AWS OpenSearch service | 30/06/2026 | 30/06/2026 | [Amazon OpenSearch Service](https://aws.amazon.com/opensearch-service/) |
| 4 | - Viết logic hệ thống gacha (quay vật phẩm) cho dự án | 01/07/2026 | 01/07/2026 | |
| 5 | - Hoàn thiện chức năng gacha và xây dựng luồng quy đổi tiền tệ | 02/07/2026 | 02/07/2026 | |
| 6 | - Hỗ trợ team viết chức năng tạo màn chơi (level generation) cho minigame | 03/07/2026 | 03/07/2026 | |


### Kết quả đạt được tuần 9:

* Đã khôi phục thành công tài khoản AWS, đảm bảo các dịch vụ của dự án tiếp tục hoạt động bình thường.
* Refactor và sửa lỗi thành công các hàm cũ, giúp hệ thống vận hành mượt mà và ít rủi ro hơn.
* Cấu trúc dữ liệu (model) trên OpenSearch được cập nhật phù hợp với yêu cầu truy vấn mới.
* Hệ thống Gacha và quy đổi tiền tệ ảo đã được lập trình hoàn chỉnh, test thành công các tỷ lệ rơi (drop rate) và luồng trừ/cộng tiền tệ.
* Phối hợp tốt với team để đẩy nhanh tiến độ hoàn thành module tạo màn chơi cho minigame.