# Hồ sơ launch v0 · Trợ lý hoàn phí LogiX-VN · Gate 2a

Một trang. Cột trạng thái chỉ nhận: **Xong, có bằng chứng · Chưa · Giả lập**. Mục nào dựa trên cột `_simulated` ghi Giả lập. Người phụ trách là một vai trò, không ghi "cả đội". Gate 2a chỉ duyệt kế hoạch pilot: không viết như thể trợ lý đã được duyệt chạy chính thức (xem quy tắc 5 trong `README.md`).

Nhóm: dimuon · Lớp: L3A

Số lấy từ `src/lab13.py` (chép trong `bang_chi_phi.md`, `pilot_plan.yaml`). Phạm vi đề xuất: chỉ `noi_dia` + `hang_nang`.

| Mục | Con số chính | Trạng thái | Người phụ trách |
| --- | --- | --- | --- |
| 1 · Chi phí mỗi việc thành công | 4.472 đ trên toàn mẫu, gấp 16,3× hoá đơn token + tool chia số yêu cầu (274,7 đ) [simulated]. Trong phạm vi `noi_dia` + `hang_nang`: 3.414 đ; cộng cố định 40 triệu/tháng ở 45.000 yêu cầu/tháng: 4.599 đ [simulated] | Giả lập | PM trợ lý hoàn phí |
| 2 · Ba yếu tố nhạy nhất | 1. Số ca làm lại ±51,8% · 2. Tỉ lệ xem lại ±40,7% · 3. Lương nhân viên +23,1%; giá token gấp đôi chỉ +5,6% [simulated] | Giả lập | PM trợ lý hoàn phí |
| 3 · So với nhân viên tự làm | Cả hệ thống, đã cộng 222 ca nhân viên làm thay: 5.865 đ/yêu cầu = 0,49× của 12.000 đ. Theo loại: `noi_dia` 0,22× · `hang_nang` 0,69× · `doi_tac` 0,85× · `quoc_te` 1,88× (thành công 27,3%), nên loại `quoc_te` và `doi_tac`. Bất lợi: xem lại 100% thì 0,98× (1,04× với 16,2 phút làm lại/ca) [simulated] | Giả lập | PM trợ lý hoàn phí |
| 4 · Chỉ số chính, chỉ số dùng, chỉ số an toàn | Chờ `chi_so.md` (E1) | Chưa | Người gắn nhãn 1 (điền E1) |
| 5 · Bảng lỗi và cách khắc phục | Chờ CP3: đồng thuận …/20, bảng khắc phục 5 ca | Chưa | Người gắn nhãn 1 (điền `bang_loi.md`) |
| 6 · Pilot plan | Chia theo nhân viên 20 + 20, ngẫu nhiên, phân tầng theo depot; mức chênh 6 điểm: 859/nhóm, DE 6,96, m ≥ 299 yêu cầu/người. Bất lợi: power 0,64 nếu tác động thật chỉ 5 điểm. 3 luật dừng (an toàn, chi phí, mức dùng); ngày quyết định 2027-01-05 | Xong, có bằng chứng | Giám đốc vận hành LogiX-VN |
| 7 · Rủi ro kinh tế | Số ca làm lại gấp đôi: 6.787 đ (+51,8%). Xem lại 100% kéo dài: 11.743 đ = 0,98×. Khối lượng còn một nửa: cố định 2.370 đ/việc, 5.784 đ = 0,48× [simulated] | Giả lập | PM trợ lý hoàn phí |

**Đề xuất:** Go · Go có điều kiện · No-go (giữ một). Go có điều kiện: ghi từng điều kiện, người phụ trách, ngày kiểm tra. No-go: ghi việc phải làm để quay lại cổng.

- ...
