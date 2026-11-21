# Bảng lỗi và cách khắc phục · Nhiệm vụ C

20 ca lỗi nằm trong `docs/Ngay13_Lab13_De_bai_hoc_vien.docx`. Năm loại theo Google PAIR: **Do người dùng · Hệ thống · Ngữ cảnh · Giới hạn hệ thống · Ngầm**. Gắn nhãn theo nguyên nhân gốc, không theo chỗ cần sửa.

## Hai bộ nhãn độc lập

Người gắn nhãn 1: Nguyễn Thanh Liêm (2A202603358) · Người gắn nhãn 2: Nguyễn Trung Anh (2A202603413) (gắn trong 8 phút, không trao đổi)

| Ca | Nhãn người 1 | Nhãn người 2 | Trùng? | Nhãn thống nhất |
| --: | --- | --- | --- | --- |
| 1 | Do người dùng | Do người dùng | Có | Do người dùng |
| 2 | Hệ thống | Hệ thống | Có | Hệ thống |
| 3 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 4 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 5 | Ngầm | Ngầm | Có | Ngầm |
| 6 | Do người dùng | Do người dùng | Có | Do người dùng |
| 7 | Hệ thống | Hệ thống | Có | Hệ thống |
| 8 | Hệ thống | Ngầm | Không | Hệ thống |
| 9 | Do người dùng | Do người dùng | Có | Do người dùng |
| 10 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 11 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 12 | Ngầm | Ngầm | Có | Ngầm |
| 13 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 14 | Do người dùng | Do người dùng | Có | Do người dùng |
| 15 | Hệ thống | Hệ thống | Có | Hệ thống |
| 16 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 17 | Ngầm | Ngầm | Có | Ngầm |
| 18 | Ngữ cảnh | Ngữ cảnh | Có | Ngữ cảnh |
| 19 | Giới hạn hệ thống | Giới hạn hệ thống | Có | Giới hạn hệ thống |
| 20 | Hệ thống | Hệ thống | Có | Hệ thống |

**Tỉ lệ đồng thuận:** 19 / 20 = 95,0%

## Quy tắc phân biệt cho các ca không trùng

Mỗi ca không trùng một câu. Đồng thuận dưới 80% thì ghi định nghĩa đã viết lại.

- **Ca 8 (Ngầm hay Hệ thống) → Hệ thống:** trợ lý trích "Điều 7.2" không có trong chính sách hiện hành, tức làm sai so với thiết kế, và trích dẫn đó hiện ngay trong câu trả lời nên ai đọc cũng thấy được; Ngầm chỉ dùng khi không ai nhận ra cho tới lúc kiểm tra mẫu.

## Bảng khắc phục cho 5 ca, mỗi loại một ca

Cách phát hiện phải đo được (event, ngưỡng, tần suất). Người phụ trách là một vai trò, không ghi "cả đội".

| Ca | Loại lỗi | Phát hiện bằng gì | Khắc phục thế nào | Ai phụ trách |
| --: | --- | --- | --- | --- |
| 1 | Do người dùng | Event `refund_ledger_write` có `ket_qua = loi_ngan_hang`, `reason = sai_so_tai_khoan`, kèm `trace_id`; đếm hằng ngày, cảnh báo khi vượt 1% số lệnh hoàn trong ngày | Trước khi tạo lệnh, kiểm tra độ dài số tài khoản theo từng ngân hàng và hiện tên chủ tài khoản để khách xác nhận; sai thì yêu cầu nhập lại, chưa tạo lệnh | PM trợ lý hoàn phí |
| 20 | Hệ thống | Truy vấn mỗi giờ trên `refund_ledger_write`: đếm `request_id` có từ 2 bản ghi `ok` trở lên; ngưỡng 0 ca, có 1 ca là bật luật dừng an toàn trong `pilot_plan.yaml` | Mỗi lệnh hoàn mang `idempotency_key` = mã vận đơn + loại hoàn; lệnh trùng khoá trả lại kết quả của lệnh đầu, không ghi sổ cái lần hai | Kỹ sư trưởng agent |
| 16 | Ngữ cảnh | Tỉ lệ phản ánh hoặc `ticket_reopened` có `reason = lam_phien` trên số tin gửi từ 22:00 đến 07:00, theo tuần; cảnh báo khi vượt 0,5% | Tin xong ngoài giờ được xếp hàng, gửi lúc 07:00; khách tự bật "nhận ngay" thì gửi luôn | Trưởng nhóm CSKH |
| 11 | Giới hạn hệ thống | Event `handoff_to_staff` có `reason = dau_vao_khong_ho_tro` (tin thoại, ảnh), đếm theo tuần; vượt 3% số yêu cầu thì đưa việc thêm chuyển giọng nói thành chữ vào kế hoạch | Báo rõ trợ lý chưa nghe được tin thoại, chuyển nhân viên kèm file thoại và mã đơn, không bắt khách gõ lại từ đầu | PM trợ lý hoàn phí |
| 12 | Ngầm | Chi phí token + tool mỗi yêu cầu tính theo depot từ `agent_run_completed`, hằng ngày; cảnh báo khi một depot vượt 1,5 lần trung vị các depot trong 3 ngày liên tiếp | Kiểm tra đủ trường trong kết quả tool; thiếu trường thì ghi lỗi tool và báo kỹ sư, không gọi lại; giới hạn số lần gọi tool trong một lần chạy | Kỹ sư trưởng agent |
