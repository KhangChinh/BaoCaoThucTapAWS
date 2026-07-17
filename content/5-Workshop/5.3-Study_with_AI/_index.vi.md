---
title : "Tích hợp AI"
date : 2026-07-17 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

# Tích hợp Trí tuệ Nhân tạo (AI) vào quản lý học tập

#### Luồng tương tác sinh Lộ trình học (Study Plan)

Tính năng Study Planner biến AI thành một chuyên gia tư vấn giáo dục cá nhân, hoạt động theo quy trình 3 bước chặt chẽ:

1. **Khởi tạo và Đính kèm tài liệu:** Người dùng bắt đầu tại tab Chat và có thể tải lên tài liệu cá nhân (PDF, DOCX, TXT). Hệ thống gọi tiến trình IPC `study:uploadFile` xuống Electron Main để phân tách văn bản (`fileParser.js`), sau đó AI tự động tóm tắt và trích xuất cấu trúc chương mục. Dữ liệu này được lưu tạm thời vào bộ nhớ Electron và hiển thị trạng thái sẵn sàng trên giao diện.
2. **Trò chuyện và Thu thập thông tin:** Qua mỗi tin nhắn (IPC `study:chat`), AI sẽ khéo léo thu thập 6 thông tin cốt lõi: Lĩnh vực, Chủ đề, Trình độ, Mục tiêu, Tổng thời gian và Thời lượng học mỗi ngày. Nếu có tài liệu đính kèm, AI tự động đọc phần tóm tắt để phản hồi bám sát nội dung sách/bài giảng. Khi đã lấy đủ các dữ liệu quan trọng, AI trả về cờ `readyToGenerate = true`.
3. **Tạo Lộ trình:** Giao diện xuất hiện nút "Tạo kế hoạch học tập". Khi người dùng kích hoạt (IPC `study:generatePlan`), AI sử dụng `PLAN_SYSTEM_PROMPT` cùng thông tin đã thu thập để sinh ra một cấu trúc JSON định dạng nghiêm ngặt. Lộ trình được chia thành 4-5 giai đoạn (phases) với thời lượng và chủ đề cụ thể, sau đó lưu cục bộ qua Electron-Store, cập nhật lên Redux và hiển thị trực quan trên giao diện Plan.

#### Luồng tương tác sinh Đề trắc nghiệm (Quiz)

Để củng cố kiến thức, hệ thống cung cấp cơ chế kiểm tra tự động dựa trên chính lộ trình và tài liệu của người dùng:

1. **Kích hoạt Quiz theo giai đoạn:** Khi hoàn thành một phase trong Lộ trình, người dùng đánh dấu hoàn tất. Hệ thống lập tức hiển thị biểu tượng Làm Quiz để khuyến khích kiểm tra kiến thức.
2. **AI Sinh Đề tự động:** Lệnh IPC `study:generateQuiz` được gửi đi. Hệ thống trích xuất các đoạn văn bản (chunks) tương ứng với phase đó từ tài liệu gốc. Thông qua `QUIZ_SYSTEM_PROMPT`, AI tạo ra đúng 10 câu hỏi trắc nghiệm khách quan. Yêu cầu hệ thống bắt buộc AI bám sát tài liệu gốc, tuyệt đối không "ảo giác" (hallucinate) hay bịa đặt kiến thức bên ngoài.
3. **Chấm điểm và Trả thưởng:** Sau khi người dùng nộp bài, hệ thống chấm điểm cục bộ và gọi API `POST /study-planner/quiz-submit` lên AWS Serverless. Backend cộng trực tiếp 10 Knowledge Point (KP) cho mỗi câu đúng vào ví, tự động tăng tiến độ các Quest ngày liên quan, và trả về dữ liệu để Client đồng bộ hiệu ứng chúc mừng.

#### Kiến trúc AI linh hoạt: Ollama (Local) và Gemini API (Cloud)

Thay vì ép buộc người dùng sử dụng một nền tảng duy nhất, hệ thống thiết kế cơ chế chuyển đổi linh hoạt giữa Ollama (AI offline) và Gemini API (AI đám mây) nhằm giải quyết 4 bài toán cốt lõi:

* **Bảo mật dữ liệu tuyệt đối (Privacy-First):** Với các tài liệu nội bộ hoặc đề cương bảo mật, Ollama cho phép toàn bộ quá trình đọc tài liệu, chat và sinh lộ trình diễn ra 100% offline trên phần cứng cá nhân. Không có bất kỳ byte dữ liệu nào bị gửi ra internet.
* **Tối ưu hóa chi phí (Zero-Cost vs. Pay-as-you-go):** Ollama cung cấp khả năng sử dụng vô hạn không tốn phí token. Ngược lại, nếu muốn dùng Gemini API, người dùng tự cấu hình API Key cá nhân, giúp kiến trúc ứng dụng không phải gánh chi phí vận hành LLM tập trung đắt đỏ.
* **Thích ứng với phần cứng người dùng:** Việc sinh JSON có cấu trúc (Structured Output) là thử thách lớn với các máy tính cấu hình yếu chạy model nhỏ cục bộ (dễ sinh lỗi format). Gemini 2.0 Flash giải quyết triệt để vấn đề này với tốc độ phản hồi 1-2 giây, Context Window cực lớn nạp trọn tài liệu hàng trăm trang và tỷ lệ xuất JSON chuẩn xác 100%. Với các máy tính có GPU mạnh, người dùng vẫn có thể chạy Llama 3 hay Qwen cục bộ mượt mà.
* **Tính đồng bộ hóa kiến trúc:** Dù dùng Local hay Cloud API, hệ thống sở hữu một lớp bọc (wrapper) tại tầng Electron. Lớp này có nhiệm vụ chuẩn hóa (normalize) mọi phản hồi từ các LLM khác nhau về cùng một cấu trúc JSON chung trước khi kết xuất lên giao diện React, đảm bảo trải nghiệm người dùng luôn nhất quán.