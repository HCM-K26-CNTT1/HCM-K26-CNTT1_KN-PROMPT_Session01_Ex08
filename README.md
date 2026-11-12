# Bài 8: Kỹ thuật Chat Summary duy trì Ngữ cảnh phiên tư vấn dài

## Phần 1. Kỹ thuật Chat Summary Block

### 1. Prompt yêu cầu AI tóm tắt

```text
Bạn là trợ lý AI quản lý dự án khuyến mãi MartX.

Hãy tóm tắt toàn bộ phiên chat lập kế hoạch
"Mùa Vàng Tri Ân" thành một Chat Summary Block.

Yêu cầu:
- Dưới 250 tokens.
- Giữ chính xác 4 thông tin:
  1. Mục tiêu chiến dịch.
  2. Ngân sách.
  3. Ý tưởng đã chốt.
  4. Việc cần làm tiếp theo.
- Chỉ giữ thông tin đã được thống nhất.
- Không tự suy diễn hoặc thêm thông tin mới.
- Viết ngắn gọn, dễ hiểu.

Xuất kết quả theo cấu trúc:
[CHAT SUMMARY BLOCK]
Mục tiêu:
Ngân sách:
Ý tưởng đã chốt:
Việc tiếp theo:
[/CHAT SUMMARY BLOCK]
```

## Phần 2. Kỹ thuật New Session Prompt

### 2.1. Chat Summary Block mẫu

```text
[CHAT SUMMARY BLOCK]
Dự án: Mùa Vàng Tri Ân – MartX.
Mục tiêu: Tăng doanh thu 20% và thu hút khách hàng mới.
Ngân sách: 200 triệu đồng.
Ý tưởng đã chốt: Giảm giá sản phẩm chủ lực, tích điểm đổi quà, minigame trên mạng xã hội.
Việc tiếp theo: Lập lịch triển khai, phân công nhân sự và xây dựng nội dung truyền thông.
[/CHAT SUMMARY BLOCK]
```

### 2.2. Prompt khởi động phiên chat mới

```text
Bạn là trợ lý AI tiếp tục hỗ trợ dự án khuyến mãi MartX.

Đây là Chat Summary Block từ phiên chat trước:

[CHAT SUMMARY BLOCK]
Dự án: Mùa Vàng Tri Ân – MartX.
Mục tiêu: Tăng doanh thu 20% và thu hút khách hàng mới.
Ngân sách: 200 triệu đồng.
Ý tưởng đã chốt: Giảm giá sản phẩm chủ lực, tích điểm đổi quà, minigame trên mạng xã hội.
Việc tiếp theo: Lập lịch triển khai, phân công nhân sự và xây dựng nội dung truyền thông.
[/CHAT SUMMARY BLOCK]

Yêu cầu:
1. Tiếp tục công việc dựa trên thông tin đã cung cấp.
2. Không đề xuất lại những ý tưởng đã chốt.
3. Không tự thay đổi mục tiêu và ngân sách.
4. Nếu thiếu thông tin, hãy hỏi lại thay vì tự suy đoán.
5. Thực hiện việc cần làm tiếp theo.
6. Trả lời ngắn gọn, mỗi lượt dưới 1.000 tokens.

Trước tiên, hãy xác nhận đã hiểu bối cảnh
và đề xuất các bước triển khai tiếp theo.
```

## Phần 3. Kết luận

Kỹ thuật Chat Summary giúp chuyển giao ngữ cảnh giữa các phiên chat mà không cần lưu trữ toàn bộ lịch sử hội thoại. Việc giữ lại 4 thông tin cốt lõi giúp AI tiếp tục công việc chính xác, tiết kiệm Token và duy trì tính liên tục của dự án.
