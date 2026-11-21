# Đặc tả chỉ số, event và rủi ro kinh tế · Nhiệm vụ E1, E2

## E1 · Đặc tả chỉ số

| Loại | Chỉ số và cách tính | Toàn mẫu (1.200 yêu cầu) | Trong phạm vi `noi_dia` + `hang_nang` (982 yêu cầu) |
| --- | --- | ---: | ---: |
| Chính | Số yêu cầu có `dong_trong_24h = 1` và `mo_lai_trong_7_ngay = 0` chia tổng yêu cầu | 994/1.200 = **82,83%** | 906/982 = **92,26%** |
| Sử dụng | Số yêu cầu được xem lại với quyết định `sua` hoặc `bo` chia số yêu cầu có `duoc_xem_lai = 1` | 48/177 = **27,12%** | 27/128 = **21,09%** |
| An toàn | Tỉ lệ lỗi lọt đến khách, đo bằng số yêu cầu có `mo_lai_trong_7_ngay = 1` chia tổng yêu cầu | 51/1.200 = **4,25%** | 39/982 = **3,97%** |
| Sử dụng bổ sung | Số yêu cầu đủ điều kiện của nhánh can thiệp mà nhân viên mở trợ lý ít nhất một lần chia tổng số yêu cầu đủ điều kiện được giao cho nhánh này | — | — |
| An toàn bổ sung | Số giao dịch hoàn có số tiền thực trả khác số tiền đúng theo chính sách chia tổng số giao dịch hoàn được kiểm tra mẫu ngẫu nhiên hằng tuần | — | — |

Ba kết quả tính thử lấy từ [`logix_requests.csv`](../../src/logix_requests.csv), là số mô tả đợt chạy thử [simulated]. Đợt chạy thử chưa có đối chứng. Pilot sẽ so sánh chỉ số chính và tỉ lệ mở lại giữa hai nhánh cùng kỳ, trong phạm vi đã đăng ký.

### Danh sách event cần ghi

Mọi event có `event_id`, `timestamp`, `request_id` và `trace_id`. Dịch vụ hoàn phí tạo `trace_id` khi tiếp nhận yêu cầu, kể cả nhánh đối chứng. Dùng `request_id` để đếm yêu cầu duy nhất và `run_id` để phân biệt các lần chạy.

| Event | Ai tạo | Thuộc tính chính | Thời điểm |
| --- | --- | --- | --- |
| `refund_request_created` | Dịch vụ hoàn phí | `trace_id`, `loai`, `depot`, `staff_id`, `arm`, `eligible` | Khi yêu cầu được tiếp nhận và gán nhân viên theo phân nhóm pilot |
| `agent_run_completed` | Trợ lý | `trace_id`, `run_id`, `attempt`, `tokens_in`, `tokens_out`, `tool_calls`, `status` | Sau mỗi lần chạy, kể cả lần lỗi |
| `assistant_opened` | Giao diện CSKH | `trace_id`, `staff_id` | Khi nhân viên chủ động mở trợ lý cho yêu cầu |
| `staff_review_decision` | Giao diện CSKH | `trace_id`, `staff_id`, `quyet_dinh` (`giu`, `sua`, `bo`), `phut_xem_lai`, `is_final` | Khi nhân viên lưu quyết định xem lại |
| `staff_rework_completed` | Giao diện CSKH | `trace_id`, `staff_id`, `phut_lam_lai`, `reason` | Khi nhân viên hoàn tất xử lý lại |
| `refund_ledger_write` | Dịch vụ sổ cái | `trace_id`, `transaction_id`, `idempotency_key`, `so_tien`, `ket_qua`, `reason` | Khi sổ cái trả kết quả cho một lần ghi hoàn tiền |
| `handoff_to_staff` | Dịch vụ hoàn phí | `trace_id`, `reason`, `loai_dau_vao` | Khi chuyển yêu cầu sang nhân viên |
| `refund_notification_sent` | Dịch vụ thông báo | `trace_id`, `channel`, `local_hour` | Khi gửi thông báo hoàn phí cho khách |
| `ticket_closed` | Hệ thống quản lý yêu cầu | `trace_id`, `closed_at` | Mỗi lần yêu cầu được đóng |
| `ticket_reopened` | Hệ thống quản lý yêu cầu | `trace_id`, `reopened_at`, `reason` | Mỗi lần yêu cầu được mở lại |
| `audit_sample_checked` | Kế toán kiểm soát | `trace_id`, `transaction_id`, `sample_id`, `so_tien_da_hoan`, `so_tien_dung`, `policy_version` | Khi hoàn tất đối soát một giao dịch trong mẫu tuần |

### Đối chiếu công thức với event

- **Chính:** Lấy mẫu số từ `refund_request_created`. Dùng lần `ticket_closed` đầu tiên để kiểm tra mốc 24 giờ kể từ lúc tiếp nhận. Với yêu cầu đã đóng, dùng `ticket_reopened` để kiểm tra 7 ngày sau khi đóng. Các yêu cầu quá 24 giờ chưa đóng không đạt chỉ số chính. Báo riêng các yêu cầu đã đóng còn thiếu thời gian theo dõi và đợi đủ 7 ngày trước khi chốt kết quả của chúng.
- **Sử dụng:** Đếm yêu cầu có `staff_review_decision` cuối cùng, phân loại theo `quyet_dinh`. Nếu có nhiều bản ghi quyết định cuối, lấy bản ghi mới nhất của yêu cầu.
- **An toàn:** Dùng cùng tập yêu cầu theo dõi, nối `ticket_closed` với `ticket_reopened` và đếm mỗi yêu cầu một lần nếu mở lại trong vòng 7 ngày sau lần đóng đầu tiên.
- **Sử dụng bổ sung:** Lọc yêu cầu đủ điều kiện thuộc nhánh can thiệp từ `refund_request_created`, rồi đếm số `request_id` có `assistant_opened`. `staff_id` của lượt mở cũng dùng để phát hiện truy cập chéo từ nhánh đối chứng.
- **An toàn bổ sung:** Dùng `audit_sample_checked`, đếm mỗi `transaction_id` một lần trong mẫu tuần và so `so_tien_da_hoan` với `so_tien_dung`. Đối soát thêm số giao dịch `ok` khác nhau trên cùng `idempotency_key` trong `refund_ledger_write` để phát hiện hoàn trùng cả khi khách gửi lại yêu cầu với `request_id` mới.

## E2 · Rủi ro kinh tế

Tác động lấy từ [bảng chi phí và độ nhạy](bang_chi_phi.md). Ngưỡng theo dõi dưới đây dùng để rà soát vận hành. Luật dừng của pilot nằm trong [kế hoạch pilot](pilot_plan.yaml).

| Rủi ro | Tác động đã tính | Dấu hiệu theo dõi | Hành động | Người phụ trách |
| --- | --- | --- | --- | --- |
| Số ca làm lại tăng gấp đôi (B1) | 6.787 đ mỗi việc thành công, tăng 51,8% trên toàn mẫu [simulated] | Tỉ lệ yêu cầu phải làm lại vượt 7% trong tuần, tính từ `staff_rework_completed` và `refund_request_created` | Rà 20 ca làm lại gần nhất hoặc toàn bộ nếu có ít hơn. Áp dụng thu hẹp phạm vi theo luật chi phí khi chạm ngưỡng trong kế hoạch pilot | PM trợ lý hoàn phí |
| Duy trì xem lại 100% (B4) | 11.743 đ mỗi việc thành công trong phạm vi pilot, bằng 0,98× mức tự làm. Nếu làm lại mất 16,2 phút/ca, chi phí lên 12.516 đ, bằng 1,04× [simulated] | Theo dõi theo tuần tỉ lệ yêu cầu được xem lại, tỉ lệ sửa hoặc bỏ và phút xem lại, làm lại đo được | Giảm xem lại theo bậc khi tỉ lệ sửa hoặc bỏ dưới 15%. Đối chiếu thời gian xem lại với mốc hòa vốn B4 tương ứng từng kịch bản | Trưởng nhóm CSKH |
