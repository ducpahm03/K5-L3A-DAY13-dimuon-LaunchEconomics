# Báo cáo cá nhân — Nguyễn Trung Anh · 2A202603413

## 1. Thông tin thành viên

- Họ tên: Nguyễn Trung Anh
- MSSV: 2A202603413
- Email: ngtranh.work@gmail.com
- GitHub: `Rising-Apocalypse`
- Nhóm: dimuon · Lớp L3A
- Vai trong nhóm: **Người gắn nhãn 2 kiêm giữ hồ sơ**

## 2. Phần việc phụ trách

- **CP3 · Bảng lỗi:** Gắn nhãn độc lập 20 ca lỗi của trợ lý hoàn phí LogiX-VN theo năm loại trong đề bài. Sau khi chốt hai bộ nhãn độc lập, so từng ca với Nguyễn Thanh Liêm (Người gắn nhãn 1) và ghi quy tắc phân biệt cho ca lệch nhãn.
- **CP4 · Kế hoạch pilot:** Đối chiếu phương án chia nhóm, cỡ mẫu và các luật dừng trong `pilot_plan.yaml` với kết quả D1 và phạm vi pilot của nhóm.
- **CP5 · Hồ sơ launch:** Tổng hợp kết quả từ đầu buổi vào `ho_so_launch_v0.md`, ghi rõ số liệu giả lập, các điều kiện cần kiểm tra và vai trò chịu trách nhiệm trước Gate 2a.

## 3. Đóng góp cụ thể

- **Gắn nhãn và đối soát.** Hai cột nhãn độc lập trùng **19/20 ca (95%)**, vượt ngưỡng 80%. Ca 8 là ca duy nhất khác nhau. Tôi gắn **Ngầm** ở lượt độc lập, còn nhãn thống nhất là **Hệ thống** vì câu trả lời viện dẫn Điều 7.2 không tồn tại trong chính sách hiện hành, dù số tiền hoàn vẫn đúng. Bảng giữ nguyên nhãn độc lập và ghi kết luận ở cột thống nhất.
- **Đối chiếu thiết kế pilot.** Kế hoạch chia ngẫu nhiên theo nhân viên, phân tầng theo depot, với 20 người dùng trợ lý và 20 người đối chứng chạy cùng thời gian. Với ICC 0,02, 20 cụm mỗi nhánh có trần cỡ mẫu hiệu dụng là 1.000, thấp hơn 1.251 cần để phát hiện chênh lệch 5 điểm phần trăm. Phương án 6 điểm phần trăm cần 859 yêu cầu hiệu dụng mỗi nhánh, tương ứng ít nhất 299 yêu cầu mỗi nhân viên theo giả định cỡ cụm bằng nhau. Nếu tác động thực là 5 điểm phần trăm thì power khoảng 0,64. Kế hoạch có ba luật dừng về an toàn, chi phí và mức sử dụng.
- **Tổng hợp đề xuất Gate 2a.** Hồ sơ đề xuất **Go có điều kiện** cho `noi_dia` và `hang_nang` tại 6 depot chạy thử. Chi phí mỗi việc thành công của hai loại này lần lượt bằng 0,22× và 0,69× mốc 12.000 đ của nhân viên tự làm. Kịch bản xem lại 100% đạt 1,04× mốc tự làm khi mỗi ca làm lại mất 16,2 phút [simulated cho các kết quả chi phí]. Các điều kiện gồm chống hoàn trùng, chỉ báo đã hoàn sau khi sổ cái xác nhận, chấp nhận đánh đổi cỡ mẫu và ghi event có `trace_id` để đo thời gian xem lại và làm lại trong pilot.

## 4. Bằng chứng

- [Bảng lỗi CP3](bang_loi.md) ghi hai bộ nhãn, tỷ lệ 19/20 và quy tắc của ca 8. Commit `639380a` ghi nhãn thống nhất. Commit `cca083b` cập nhật vai trò và thứ tự cột nhãn.
- [Kế hoạch pilot](pilot_plan.yaml) và [mã tính D1](../../src/lab13.py) ghi các giả định cỡ mẫu, cách chia nhóm và luật dừng do nhóm xây dựng.
- [Hồ sơ launch v0](ho_so_launch_v0.md) ghi phần tổng hợp và đề xuất qua hai commit `ab6af8d` và `eb7871b`. [Bảng chi phí](bang_chi_phi.md) là nguồn đối chiếu các số ở A3 và B4.

## 5. Công cụ AI đã dùng

- Dùng ChatGPT (Codex) để hỗ trợ soạn và rà soát báo cáo cá nhân dựa trên tài liệu và các file của nhóm. Phần đối chiếu dùng cột nhãn theo vai trò hiện hành trong `TEAM.md`, đếm lại số ca trùng và kiểm tra ca 8 với đề bài. Các số về chi phí và cỡ mẫu được đối chiếu với kết quả chạy `src/lab13.py`.

- Dùng Claude Code (Anthropic) để cài môi trường Python, giải thích đề, điền bản nháp các mục số liệu và đề xuất trong `ho_so_launch_v0.md`, ghép hai cột nhãn vào `bang_loi.md`, đếm số ca trùng, và thao tác commit, pull, push. Nhãn 20 ca do tôi tự gắn độc lập, không dùng AI. Mọi con số Claude điền được lấy từ output `src/lab13.py`, và tôi đã đối chiếu lại với `bang_chi_phi.md` và `pilot_plan.yaml`.

## 6. Tự đánh giá

- Tôi đã ghi được bộ nhãn độc lập, lý do thống nhất ca 8 và các đánh đổi quan trọng của đề xuất pilot. Ba chỉ số trong hồ sơ là số mô tả đợt chạy thử. Tác động của trợ lý cần được ước lượng từ so sánh với nhóm đối chứng trong pilot.
- Mục 5 của hồ sơ launch còn cần cập nhật số đồng thuận. Bảng khắc phục của nhóm vẫn cần đủ năm ca đại diện, với cách phát hiện đo được và một vai trò phụ trách cho mỗi ca.
