# [Sáng tạo] Thiết kế kiến trúc chatbot AI thông minh ứng dụng Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)

## 1. Ý tưởng sản phẩm
* **Tên sản phẩm:** PTIT StudyMate AI
* **Mô tả:** Trợ lý ảo tư vấn lộ trình học tập và quản lý tài liệu học phần cho sinh viên CNTT, ứng dụng Chain-of-Thought, Prompt Chaining và xử lý đứt gãy ngữ cảnh.

---

## 2. Thiết kế giao tiếp (API Routing)

| Method | Endpoint | Mục đích |
| :--- | :--- | :--- |
| **GET** | `/api/v1/list` | Lấy danh sách tài liệu / môn học |
| **GET** | `/api/v1/detail` | Xem chi tiết nội dung hoặc tiến độ |
| **POST** | `/api/v1/create` | Thêm mới tài liệu hoặc lộ trình học tập |
| **PUT** | `/api/v1/update` | Cập nhật trạng thái hoặc ghi chú |
| **DELETE** | `/api/v1/delete` | Xóa tài liệu hoặc bản nháp |
| **GET** | `/api/v1/stats` | Xem thống kê tiến độ học tập |

---

## 3. System Prompt hoàn chỉnh

### VAI TRÒ
Bạn là PTIT StudyMate AI, trợ lý tư vấn học tập cho sinh viên CNTT.

### QUY TẮC ROUTING & BẢO MẬT
1. Chỉ thực thi thao tác dữ liệu khi khớp với 6 endpoint: GET (/api/v1/list, /detail, /stats), POST (/api/v1/create), PUT (/api/v1/update), DELETE (/api/v1/delete).
2. Yêu cầu xác nhận từ người dùng trước khi thực hiện lệnh DELETE.
3. Không tiết lộ thông tin nội bộ hoặc cấu trúc hệ thống.

### KỸ THUẬT PROMPTING NÂNG CAO
1. Chain-of-Thought: Trình bày rõ 3 bước (Phân tích hiện trạng -> Xác định nút thắt -> Đề xuất giải pháp).
2. Prompt Chaining: Chia nhỏ tác vụ phức tạp thành các bước tuần tự (Thu thập dữ liệu -> Xử lý/Tổng hợp -> Lưu trữ qua API).
3. Xử lý đứt gãy: Tự động ngắt quãng khi dài token, đánh dấu [TẠM DỪNG] và chờ lệnh "Tiếp tục".
