# Báo cáo cá nhân — PhamHuuDuc-2A202603380

## 1. Thông tin thành viên

- Họ tên: Phạm Hữu Đức
- MSSV: 2A202603380
- Email: phamduc31103@gmail.com
- Vai trong nhóm: **Người kiểm số (CP1–CP2) & Lập trình viên đổi vai tiếp quản code (CP4)**

## 2. Phần việc phụ trách

- **Nhiệm vụ A (CP1):** Tính tay độc lập 3 phép thử đáp án biết trước ($p = 0,8$), kiểm tra chéo các công thức thành phần của mô hình chi phí trong `src/lab13.py` và bảng A2 (`report/team/bang_chi_phi.md`).
- **Nhiệm vụ B (CP2):** Phân tích và kiểm tra các kịch bản độ nhạy B1–B4; kiểm tra tính cộng tuyến tính ở kịch bản đổi một cặp B2; phân tích nghịch lý tối ưu chi phí cả hệ thống ở kịch bản giới hạn số lần chạy B3.
- **Nhiệm vụ D (CP4):** Tiếp quản vai viết code sau giờ giải lao; kiểm soát hàm tính cỡ mẫu `co_mau`, hệ số thiết kế `he_so_thiet_ke` trong `src/lab13.py` và rà soát các tham số trong `report/team/pilot_plan.yaml`.

## 3. Đóng góp cụ thể

- Tính toán độc lập 3 giá trị kiểm thử chuẩn: $1,20$ (chạy tối đa 2 lần), $1,25$ (chạy đến khi đúng), $1,25$ (hệ số chi phí tối đa 3 lần).
- Xác nhận số liệu A2 khớp với trace: chi phí token (245.585 đ), tool (84.000 đ), xem lại giả lập (1.780.000 đ), làm lại giả lập (2.264.000 đ), tổng chi phí 4.373.585 đ, chi phí mỗi việc thành công 4.472 đ [simulated].
- Chỉ ra giờ nhân viên chiếm tới 92,5% tổng chi phí và CPS gấp 16,3 lần hóa đơn token/tool chia cho số yêu cầu.
- Chứng minh phương án giới hạn 2 lần chạy là tối ưu nhất cho toàn công ty (6.901.220 đ so với 7.449.781 đ của 1 lần và 7.037.585 đ của 3 lần).
- Xác nhận cỡ mẫu cho thử nghiệm RCT phân cụm: với 40 nhân viên không thể đo được mức chênh 5 điểm với power 0,8, qua đó chốt mức đánh đổi MDE 6 điểm ($n = 859$ yêu cầu/nhóm).

## 4. Bằng chứng

- File báo cáo chi phí: [`report/team/bang_chi_phi.md`](file:///F:/vinai/K5-L3A-DAY13-dimuon-LaunchEconomics/report/team/bang_chi_phi.md)
- Kế hoạch pilot: [`report/team/pilot_plan.yaml`](file:///F:/vinai/K5-L3A-DAY13-dimuon-LaunchEconomics/report/team/pilot_plan.yaml)
- Các commit kiểm tra số liệu, gộp nhánh và đồng bộ code trên repo: `K5-L3A-DAY13-dimuon-LaunchEconomics`.

## 5. Công cụ AI đã dùng

- Dùng trợ lý AI hỗ trợ rà soát công thức tính hệ số thiết kế cụm $DE = 1 + (m - 1) \times ICC$ và kiểm tra cú pháp yaml.
- Tự kiểm tra lại toàn bộ kết quả bằng lệnh chạy Python cục bộ `python lab13.py` và đối chiếu từng dòng số liệu trong file markdown.

## 6. Tự đánh giá

- Hoàn thành đầy đủ trách nhiệm của Người kiểm số và vai trò lập trình viên tiếp quản.
- Đảm bảo tính toán chính xác sai số ≤ 2% so với đáp án chuẩn của giảng viên, hỗ trợ nhóm giữ đúng tiến độ các checkpoint.
