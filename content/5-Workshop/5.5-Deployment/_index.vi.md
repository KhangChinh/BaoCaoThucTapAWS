---
title : "Triển khai và Kết quả"
date : 2026-07-17 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

# Triển khai, Vận hành và Kết quả đạt được

#### 1. Chiến lược Quản lý mã nguồn và Triển khai (Deployment)

Để đảm bảo tính độc lập, dễ dàng bảo trì và mở rộng, toàn bộ mã nguồn của dự án Uchimi được chia tách thành hai kho lưu trữ (GitHub repositories) riêng biệt:
*   **Frontend Repository:** Chứa mã nguồn của ứng dụng máy tính (ReactJS + Electron), chịu trách nhiệm quản lý UI/UX, tích hợp AI Local (Ollama) và giao tiếp với Backend.
*   **Backend Repository:** Chứa toàn bộ logic nghiệp vụ Serverless (Node.js 20.x) và cấu hình hạ tầng `serverless.yml`[cite: 4].

**Quy trình triển khai tự động (Infrastructure as Code):**
Việc đưa hệ thống Backend lên môi trường đám mây AWS được thực hiện thông qua Serverless Framework. Thay vì click tạo thủ công từng dịch vụ, toàn bộ hạ tầng được đóng gói và đẩy lên AWS (region `ap-southeast-1`) chỉ bằng một câu lệnh duy nhất trên Terminal[cite: 4]:
```bash
serverless deploy
```
Quá trình này tự động biên dịch code (esbuild), tạo ra các CloudFormation Templates và cung cấp (provision) tài nguyên thực tế một cách đồng bộ[cite: 4].

![Log triển khai thành công trên Terminal](/images/5.5-Deploy/terminal-deploy-success.png)
> *(Yêu cầu ảnh `terminal-deploy-success.png`: Chụp màn hình Terminal (VS Code hoặc CMD) lúc chạy lệnh `serverless deploy` chạy xong 100%, hiển thị dòng chữ Success và danh sách các endpoints/functions được in ra màn hình).*

**Bảo mật Biến môi trường (Environment Variables):**
Để bảo vệ các thông tin nhạy cảm như khóa API của Algolia (`ALGOLIA_WRITE_KEY`), thông tin Cognito (`COGNITO_USER_POOL_ID`), hệ thống sử dụng plugin `useDotenv: true` để load an toàn các biến từ file `.env` cục bộ[cite: 4]. Code đẩy lên GitHub hoàn toàn sạch bóng các thông tin bảo mật này, triệt tiêu rủi ro lộ lọt dữ liệu.

#### 2. Vận hành hệ thống thực tế trên AWS Cloud

Sau khi triển khai thành công, kiến trúc Serverless của Uchimi chính thức đi vào hoạt động. Dưới đây là các minh chứng vận hành thực tế:

**Quản lý Tài nguyên với AWS CloudFormation:**
Toàn bộ các tài nguyên (Lambda, API Gateway, IAM Roles, CloudWatch Logs) đều được AWS CloudFormation gom chung thành một Stack. Điều này giúp dễ dàng theo dõi trạng thái và xóa sạch tài nguyên (rollback) chỉ bằng một thao tác nếu có lỗi, không để lại tài nguyên rác "ngốn" tiền.

![Danh sách tài nguyên CloudFormation](/images/5.5-Deploy/cloudformation-resources.png)
> *(Yêu cầu ảnh `cloudformation-resources.png`: Đăng nhập AWS > vào CloudFormation > chọn Stack `aws-uchimi-dev` > chọn tab **Resources**. Chụp màn hình danh sách dài các tài nguyên (AWS::Lambda::Function, AWS::Logs::LogGroup...) đang ở trạng thái CREATE_COMPLETE).*

**Hệ thống API Gateway và AWS Lambda:**
Cổng giao tiếp API Gateway hoạt động ổn định với 25 routes được định tuyến chính xác[cite: 4]. Hệ thống phân tách rõ ràng thành 20 hàm Lambda (như User, Gacha, Minigame, Quest...)[cite: 4] theo nguyên tắc Đơn trách nhiệm (Single Responsibility). 

![Danh sách Lambda Functions và API Gateway](/images/5.5-Deploy/api-lambda-console.png)
> *(Yêu cầu ảnh `api-lambda-console.png`: Chụp màn hình Console của AWS Lambda (danh sách các hàm có tiền tố `aws-uchimi-dev-...`) HOẶC chụp màn hình Amazon API Gateway hiển thị sơ đồ các Routes (GET, POST) của dự án).*

**Lưu trữ dữ liệu phi tập trung với Amazon DynamoDB:**
Hệ cơ sở dữ liệu NoSQL với 8 bảng phân tán vận hành với tốc độ truy xuất mili-giây. Để đảm bảo tính toàn vẹn dữ liệu cho các giao dịch phức tạp (ví dụ: vừa trừ tiền vừa thêm item vào túi đồ), hệ thống sử dụng các hàm `TransactWriteItems` và `BatchWriteItem` một cách triệt để[cite: 4].

![Dữ liệu người dùng trên DynamoDB](/images/5.5-Deploy/dynamodb-tables.png)
> *(Yêu cầu ảnh `dynamodb-tables.png`: Đăng nhập AWS > vào DynamoDB > Explore items > chọn bảng User (hoặc Inventory/Quest). Chụp màn hình hiển thị các dòng dữ liệu JSON thực tế của người dùng đang được lưu trữ).*

#### 3. Tối ưu hóa Hiệu năng và Chi phí

Trong quá trình triển khai thực tế, dự án đã áp dụng các chiến lược tinh chỉnh sâu để đạt hiệu quả cao nhất:
*   **Tối ưu tài nguyên Lambda:** Thay vì để mặc định, bộ nhớ của toàn bộ các hàm Lambda được quy hoạch ở mức `512 MB`[cite: 4]. Đây là điểm "ngọt" (sweet spot) giúp cân bằng hoàn hảo giữa tốc độ thực thi nhanh và chi phí thấp.
*   **Scale-to-Zero (Chi phí 0 đồng khi rảnh rỗi):** Lợi thế lớn nhất của Serverless là khi không có người dùng sử dụng ứng dụng, số lượng máy chủ chạy ngầm bằng 0, đồng nghĩa với việc hệ thống hoàn toàn không phát sinh chi phí duy trì cố định (Pay-as-you-go).
*   **Giới hạn chịu tải (Throttling):** Để chống lại các đợt tấn công DDoS hoặc spam request, API Gateway được cấu hình Throttling giới hạn nghiêm ngặt ở mức 50 requests/giây và 20 concurrent requests[cite: 4].

#### 4. Kết luận về tính khả thi

Thông qua việc kết hợp chặt chẽ giữa Frontend Electron và Backend Serverless AWS, dự án Uchimi đã chứng minh được tính khả thi kỹ thuật vượt trội:
1.  **Đồng bộ mượt mà:** Sự kết hợp giữa API `POST /sync-all` và hệ thống cache cục bộ (Redux/Electron-store) giúp ứng dụng phản hồi gần như tức thời ngay cả khi mạng yếu.
2.  **Môi trường Gamification công bằng:** Thuật toán Anti-cheat phía Server bảo vệ thành công bảng xếp hạng khỏi các phần mềm thứ ba.
3.  **Tự động hóa toàn diện:** Các tác vụ định kỳ như cập nhật Leaderboard, làm mới Cửa hàng (Shop), tự động quy đổi Gacha trùng lặp, và đồng bộ tìm kiếm Algolia qua Streams hoạt động chính xác 100% không cần con người can thiệp.