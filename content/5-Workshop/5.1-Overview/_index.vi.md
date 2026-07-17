---
title: "Bối cảnh, Mục tiêu và Bài toán kỹ thuật"
date: 2026-07-17 
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

# Bối cảnh và Bài toán thiết kế hệ thống

Bộ não con người tự nhiên có xu hướng tìm kiếm các phần thưởng tức thì (dopamine) từ mạng xã hội hoặc trò chơi giải trí, trong khi kết quả của việc học thường mất thời gian dài mới hiện rõ. Khi học một mình, người học dễ cảm thấy cô đơn, thiếu động lực cạnh tranh và không có hệ thống đo lường tiến độ trực quan. 

#### Mục tiêu dự án và đối tượng

Ứng dụng được thiết kế linh hoạt để phục vụ đa dạng tệp người dùng:
* **Học sinh, sinh viên:** Có thể tận dụng chế độ học tập kỷ luật (Rank mode)[cite: 1] và các phiên kiểm tra kiến thức tự động (Quiz) từ Study Planner để chạy deadline, ôn thi hiệu quả.
* **Người đi làm:** Hưởng lợi từ tính năng quản lý chuỗi ngày học liên tục (streak) và tự do lập kế hoạch học tập cá nhân hóa qua AI Chatbot khi tự học ngoại ngữ hoặc lập trình.

**Mục tiêu cốt lõi** của dự án là "hack" vào hệ thống phần thưởng của não bộ, biến kỷ luật khô khan thành một bản năng tự nhiên. Thông qua hệ thống nhiệm vụ hàng ngày[cite: 1, 3] và bảng xếp hạng[cite: 1, 3], nhằm thúc đẩy người dùng khao khát ngồi vào bàn học để hoàn thành mục tiêu, tìm thấy niềm vui trong quá trình tích lũy kiến thức thay vì coi đó là gánh nặng.

#### Bài toán kỹ thuật cốt lõi:
1.  **Toàn vẹn dữ liệu (Data Integrity):** Với 4 loại tiền tệ luân chuyển liên tục, làm sao để tránh việc "nhân bản vật phẩm" hoặc "âm tiền" khi người dùng cố tình gửi request spam cùng lúc?
2.  **Server Authority (Chống gian lận):** Mọi logic quan trọng (xác suất Gacha, kết quả Minigame, trạng thái phiên học) phải nằm ở Server, không được tin Client.
3.  **Offline-First:** Trải nghiệm Desktop phải mượt mà. Ứng dụng phải nạp dữ liệu từ Cache (Hydration) ngay tức thì khi mở máy, sau đó mới đồng bộ với Server âm thầm.