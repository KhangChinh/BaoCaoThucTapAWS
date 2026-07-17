---
title: "Workshop"
date: 2026-07-17
weight: 5
chapter: true
pre: " <b> 5. </b> "
---

# Uchimi StudyGamification: Kiến tạo thói quen học tập thông qua AI và hệ sinh thái Gamification

Chào mừng bạn đến với tài liệu kỹ thuật của dự án **Uchimi StudyGamification**. Dự án được xây dựng với kiến trúc **ReactJS + Electron** ở phía Client và **AWS Serverless** ở phía Server, hướng đến mục tiêu biến quá trình tự học thành một trải nghiệm học tập mang tính tương tác, duy trì động lực và tạo dựng thói quen lâu dài.

## Tổng quan

Một trong những thách thức lớn nhất của quá trình tự học không nằm ở việc tiếp cận kiến thức, mà ở khả năng **duy trì sự tập trung** và **xây dựng tính kỷ luật trong thời gian dài**. Người học rất dễ bị phân tâm hoặc mất động lực, khiến việc học bị gián đoạn và khó hình thành thói quen bền vững.

**Uchimi StudyGamification** được phát triển nhằm giải quyết vấn đề này bằng cách kết hợp giữa **Gamification**, **Trí tuệ nhân tạo (AI)** và các cơ chế hỗ trợ học tập hiện đại. Thay vì xem việc học là một nhiệm vụ mang tính bắt buộc, dự án hướng tới việc biến mỗi phiên học thành một trải nghiệm có mục tiêu, có phản hồi và có phần thưởng.

Hệ thống kết hợp các phiên học tập tập trung, chuỗi nhiệm vụ hằng ngày, cơ chế phần thưởng tức thời cùng trợ lý AI để tạo động lực liên tục cho người dùng. Những cơ chế này giúp củng cố vòng lặp **Hành động → Phản hồi → Phần thưởng**, từ đó góp phần hình thành thói quen học tập một cách tự nhiên và bền vững.

Bên cạnh việc cải thiện trải nghiệm người dùng, dự án còn tập trung giải quyết nhiều bài toán kỹ thuật quan trọng trong quá trình xây dựng một ứng dụng Desktop kết hợp Cloud, bao gồm:

- Đồng bộ dữ liệu theo mô hình **Offline-First**.
- Đảm bảo tính nhất quán dữ liệu thông qua các giao dịch **ACID** và xử lý **Race Condition**.
- Xây dựng cơ chế **Anti-cheat Stateless** nhằm hạn chế gian lận mà không phụ thuộc vào trạng thái phiên làm việc.
- Tích hợp **Edge AI** để hỗ trợ các tính năng AI ngay trên thiết bị người dùng, giảm độ trễ và tăng khả năng hoạt động ngoại tuyến.

## Mục lục kiến trúc

1. [Bối cảnh, Mục tiêu và Bài toán kỹ thuật](5.1-Overview/)
2. [Kiến trúc hệ thống](5.2-Architecture/)
3. [Học tập cùng AI](5.3-Study_with_AI/)
4. [Gamification](5.4-Gamification/)
5. [Triển khai và Vận hành](5.5-Deployment/)
6. [Định hướng phát triển](5.6-Direction/)

## Mã nguồn

- **Frontend:** https://github.com/KhangChinh/AWSStudy-Play
- **Backend:** https://github.com/KhangChinh/AWSServerless