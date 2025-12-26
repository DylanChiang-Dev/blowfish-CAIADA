---
title: "[Báo cáo] Phân tích chuyên sâu Báo cáo Hiện trạng AI 2024 của OpenRouter"
date: 2025-10-27T10:00:00+08:00
description: "Dựa trên dữ liệu thực nghiệm 100 nghìn tỷ Token từ OpenRouter, báo cáo này phân tích sự chuyển đổi mô hình từ 'tạo dự đoán' sang 'lập luận logic', cùng sự trỗi dậy của các mô hình nguồn mở và Agentic Inference."
summary: "OpenRouter công bố báo cáo 'State of AI', tiết lộ sự thống trị của các mô hình lập luận o1, các mô hình nguồn mở chiếm 1/3 thị phần và Agentic Inference trở thành cốt lõi của hệ sinh thái mới."
tags: ["AI", "OpenRouter", "Đọc báo cáo", "Mô hình lập luận", "o1", "DeepSeek", "Agent"]
categories: ["Tài liệu kỹ thuật"]
showAuthor: false
showHero: true
heroStyle: "big"
featureimage: "img/news/openrouter_state_of_ai_2024_cover.png"
---

## Lời mở đầu

Năm 2024 đánh dấu một bước ngoặt căn bản trong quá trình tiến hóa và ứng dụng thực tế của các mô hình ngôn ngữ lớn (LLM). Bằng cách phân tích hơn **100 nghìn tỷ (100 Trillion) Token** tương tác thực tế trên nền tảng của mình, OpenRouter đã công bố báo cáo "State of AI". Nghiên cứu này không chỉ là đánh giá ngang hàng mà còn mang lại cái nhìn sâu sắc về cách các nhà phát triển và người dùng cuối thực sự sử dụng AI trong thực tế.

## Tóm tắt các phát hiện chính

1.  **Sự trỗi dậy của các mô hình lập luận (Reasoning Models)**: Kể từ khi o1 chính thức ra mắt vào tháng 12 năm 2024, AI đang chuyển dịch từ dự đoán mô hình đơn lẻ sang lập luận và cân nhắc đa bước.
2.  **Định hình lại bối cảnh nguồn mở**: Các mô hình nguồn mở (OSS) hiện chiếm **1/3** tổng lượng sử dụng, trong đó các mô hình Trung Quốc Đại lục (DeepSeek, Qwen) cho thấy hiệu suất đáng kinh ngạc.
3.  **Agentic Inference**: AI không còn chỉ là một hộp thoại chat mà đóng vai trò là các "Agent" thực hiện nhiệm vụ và gọi công cụ. Chế độ Agentic đã trở thành mặc định cho các môi trường triển khai.
4.  **Hiệu ứng Cinderella**: Các nhóm người dùng sớm cho thấy tỷ lệ giữ chân và lòng trung thành cực kỳ cao.

---

## Chương 1: Từ Dự đoán đến Lập luận — Điểm uốn o1

Trước cuối năm 2024, các hệ thống SOTA chủ yếu là các trình dự đoán tự hồi quy đơn bước. Sự xuất hiện của o1 (Strawberry) đã phá vỡ giới hạn này:
-   **Tính toán nội bộ**: Các mô hình lập luận mở rộng tính toán trong thời gian suy luận thông qua việc cân nhắc đa bước nội bộ, lập kế hoạch tiềm ẩn và tinh chỉnh lặp đi lặp lại trước khi đưa ra kết quả.
-   **Bước nhảy vọt về năng lực**: Điều này cho phép cải thiện hệ thống trong lập luận toán học, tính nhất quán logic và ra quyết định đa bước.
-   **Chuyển đổi mô hình**: Lập luận không còn chỉ là một quy trình được "mô tả" mà là một logic cốt lõi được nhúng trong kiến trúc.

## Chương 2: Nguồn mở vs Độc quyền — Trạng thái bình thường mới của sự đa nguyên

Báo cáo cho thấy một sự cân bằng động giữa các mô hình nguồn mở và độc quyền ở mức xấp xỉ **30% vs 70%**:
-   **Sự tăng trưởng ổn định của OSS**: Các mô hình nguồn mở mang lại lợi thế về hiệu quả chi phí, tính minh bạch và khả năng tùy chỉnh, trở thành một phần quan trọng của ngăn xếp đa mô hình (Multi-model stack).
-   **Sự trỗi dậy mạnh mẽ của các mô hình Trung Quốc**: Chu kỳ phát hành dày đặc của các mô hình như DeepSeek V3 và Qwen đã đẩy thị phần sử dụng của OSS Trung Quốc lên gần **30%** trong một số tuần. Thị phần trung bình hàng tuần 13,0% cho thấy năng lực cạnh tranh kỹ thuật mạnh mẽ.

## Chương 3: Sự trỗi dậy của Agentic Inference

Việc sử dụng LLM đang chuyển từ "hoàn thành văn bản đơn lượt" sang "quy trình làm việc đa bước, tích hợp công cụ":
-   **Khối lượng công việc tập trung lập luận**: Các tác vụ yêu cầu lập luận cường độ cao hiện chiếm gần một nửa tổng lượng sử dụng.
-   **Hành vi gọi công cụ (Tool-calling)**: Các nhà phát triển ngày càng sử dụng các mô hình như các thành phần cốt lõi trong các hệ thống tự động hóa lớn hơn.
-   **Thay đổi hình thái tương tác**: Dữ liệu cho thấy các câu lệnh (Prompt) và kết quả (Completion) đang trở nên dài hơn và phức tạp hơn. Báo cáo dự đoán: **Suy luận của Agent có thể đã hoặc sẽ sớm vượt qua suy luận của con người.**

---

## Chương 4: Hành vi người dùng và Phân tích địa lý

### 1. Các danh mục thống trị bất ngờ
-   **Nhập vai sáng tạo (Creative Roleplay)**: Dẫn đầu một cách đáng ngạc nhiên so với nhiều tác vụ năng suất vốn được cho là sẽ chiếm ưu thế.
-   **Hỗ trợ lập trình (Coding Assistance)**: Vẫn là một ứng dụng giá trị cao cốt lõi của AI.
-   **Sự đa dạng của phân loại**: Người dùng tương tác với LLM cho một loạt các nhiệm vụ đa diện vượt ra ngoài các chức năng "trợ lý" đơn giản.

### 2. Hiệu ứng giữ chân Cinderella "Glass Slipper"
Nghiên cứu xác định các "nhóm người dùng nền tảng" — những người dùng sớm có sự gắn kết kéo dài hơn nhiều so với các nhóm sau này. Hiệu ứng này gợi ý rằng AI đã phát triển độ sâu và sự gắn bó không thể thay thế cho các phân khúc cụ thể.

### 3. Biến động địa lý
-   Việc sử dụng toàn cầu cho thấy sự khác biệt rõ rệt theo khu vực.
-   Thị phần châu Á tiếp tục mở rộng, phản ánh sự phi tập trung hóa của các nguồn lực và nhu cầu tính toán toàn cầu.

---

## Kết luận và Triển vọng tương lai

Mô hình o1 không kết thúc sự cạnh tranh; nó mở rộng không gian thiết kế. Lĩnh vực này đang chuyển từ "điểm số trên bảng xếp hạng" sang "hoàn thành nhiệm vụ thực tế".
-   **Tư duy hệ thống**: Sự tập trung chuyển sang vận hành xuất sắc và điều phối đa mô hình.
-   **Nguồn lực toàn cầu**: LLM đã trở thành một tài sản tính toán toàn cầu thực sự với một hệ sinh thái đa dạng về cấu trúc.

---

> [!IMPORTANT]
> **Link báo cáo gốc:** [OpenRouter State of AI](https://openrouter.ai/state-of-ai)
> **Tải xuống PDF:** [State-of-AI.pdf](https://openrouter.ai/assets/State-of-AI.pdf)
