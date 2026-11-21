# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Một trang. Cột trạng thái chỉ nhận: **Xong, có bằng chứng · Chưa · Giả lập**. Mục nào dựa trên cột `_simulated` ghi Giả lập. Người phụ trách là một vai trò, không ghi "cả đội". Gate 2a chỉ duyệt kế hoạch pilot: không viết như thể trợ lý đã được duyệt chạy chính thức (xem quy tắc 5 trong `README.md`).

Nhóm: dimuon · Lớp: L3A

Số lấy từ `src/lab13.py` (chép trong `bang_chi_phi.md`, `pilot_plan.yaml`). Phạm vi đề xuất: chỉ `noi_dia` + `hang_nang`.

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | 4.472 đ trên toàn mẫu, gấp 16,3× hoá đơn token + tool chia số yêu cầu (274,7 đ) [simulated]. Trong phạm vi `noi_dia` + `hang_nang`: 3.414 đ; cộng cố định 40 triệu/tháng ở 45.000 yêu cầu/tháng: 4.599 đ [simulated] | Giả lập | PM trợ lý hoàn phí |
| 2 · Ba yếu tố nhạy nhất | 1. Số ca làm lại ±51,8% · 2. Tỉ lệ xem lại ±40,7% · 3. Lương nhân viên +23,1%; giá token gấp đôi chỉ +5,6% [simulated] | Giả lập | PM trợ lý hoàn phí |
| 3 · So với nhân viên tự làm | Cả hệ thống, đã cộng 222 ca nhân viên làm thay: 5.865 đ/yêu cầu = 0,49× của 12.000 đ. Theo loại: `noi_dia` 0,22× · `hang_nang` 0,69× · `doi_tac` 0,85× · `quoc_te` 1,88× (thành công 27,3%), nên loại `quoc_te` và `doi_tac`. Bất lợi: xem lại 100% thì 0,98× (1,04× với 16,2 phút làm lại/ca) [simulated] | Giả lập | PM trợ lý hoàn phí |
| 4 · Chỉ số chính, chỉ số dùng, chỉ số an toàn | Chỉ số trong đợt chạy thử (chưa có đối chứng, không phải tác động của trợ lý): chính 82,83% (994/1.200) đóng trong 24 giờ và không mở lại 7 ngày · dùng: bỏ qua gợi ý 27,12% (48/177 ca được xem lại) · an toàn: mở lại 7 ngày 4,25% (51/1.200). Trong phạm vi: 92,26% · 21,09% · 3,97% | Xong, có bằng chứng | Trưởng nhóm CSKH |
| 5 · Bảng lỗi và cách khắc phục | Hai bộ nhãn độc lập trùng 19/20 = 95% (≥ 80%); ca lệch duy nhất là ca 8, chốt Hệ thống. Bảng khắc phục 5 ca, mỗi loại một ca (ca 1, 20, 16, 11, 12), mỗi ca có cách phát hiện đo được bằng event, ngưỡng, tần suất và một vai trò phụ trách | Xong, có bằng chứng | PM trợ lý hoàn phí |
| 6 · Pilot plan | Chia theo nhân viên 20 + 20, ngẫu nhiên, phân tầng theo depot; mức chênh 6 điểm: 859/nhóm, DE 6,96, m ≥ 299 yêu cầu/người. Bất lợi: power 0,64 nếu tác động thật chỉ 5 điểm. 3 luật dừng (an toàn, chi phí, mức dùng); ngày quyết định 2027-01-05 | Xong, có bằng chứng | Giám đốc vận hành LogiX-VN |
| 7 · Rủi ro kinh tế | Số ca làm lại gấp đôi: 6.787 đ (+51,8%). Xem lại 100% kéo dài: 11.743 đ = 0,98×. Khối lượng còn một nửa: cố định 2.370 đ/việc, 5.784 đ = 0,48× [simulated] | Giả lập | PM trợ lý hoàn phí |

**Đề xuất: Go có điều kiện** cho pilot `noi_dia` + `hang_nang` ở 6 depot chạy thử, chia theo nhân viên 20 + 20. Con số bất lợi đã tính: xem lại 100% chỉ còn 0,98× (1,04× với 16,2 phút làm lại) [simulated]; power 0,64 nếu tác động thật chỉ 5 điểm. Điều kiện:

- Có khoá chống trùng và chỉ báo "đã hoàn" khi sổ cái trả ok (ca 7, 20). Phụ trách: Kỹ sư trưởng agent · Kiểm tra: 2026-12-05.
- Ký chấp nhận mức chênh 6 điểm (859/nhóm, m ≥ 299 yêu cầu/người, power 0,64 ở mức 5 điểm). Phụ trách: Giám đốc vận hành LogiX-VN · Kiểm tra: 2026-12-07.
- Bật đủ event có `trace_id`; thay phút xem lại, làm lại simulated bằng phút đo thật sau tuần 1. Phụ trách: Kỹ sư trưởng agent · Kiểm tra: 2026-12-14.
- Giảm xem lại theo bậc khi tỉ lệ sửa + bỏ < 15%, mục tiêu mỗi lần xem lại ≤ 5 phút (hoà vốn 5,1 phút, B4). Phụ trách: Trưởng nhóm CSKH · Kiểm tra: 2026-12-21.
