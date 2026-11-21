# Báo cáo nhóm dimuon Lab 13

## 1. Thông tin nhóm

Nhóm **dimuon**, lớp **L3A**. Thành viên gồm Trần Anh Tú, Phạm Hữu Đức, Nguyễn Thanh Liêm và Nguyễn Trung Anh. [Phân công nhóm](../../TEAM.md).

## 2. Mục tiêu và cách tiếp cận

Nhóm đề xuất **Go có điều kiện** tại Gate 2a cho pilot trợ lý hoàn phí LogiX-VN, giới hạn ở yêu cầu nội địa và hàng nặng tại 6 depot chạy thử. Nhóm dùng dữ liệu giả lập gồm 1.200 yêu cầu và 1.624 lần chạy để ước tính chi phí, phân tích lỗi và thiết kế thử nghiệm có đối chứng.

## 3. Giải pháp

| Nhiệm vụ | Cách làm và bằng chứng |
| --- | --- |
| A · Chi phí | Cộng token, tool, thời gian xem lại và làm lại trên toàn bộ mẫu, kể cả chi phí từ lần chạy lỗi. Chia cho số yêu cầu thành công để tính chi phí mỗi việc thành công. [Mã tính](../../src/lab13.py) · [Bảng chi phí](bang_chi_phi.md) |
| B · Độ nhạy | Thay đổi từng yếu tố và so chi phí cả hệ thống khi giới hạn 1, 2 hoặc 3 lần chạy. Tính thêm kịch bản xem lại 100%. [Bảng độ nhạy](bang_chi_phi.md#b1--đổi-từng-yếu-tố) |
| C · Bảng lỗi | Hai người gắn nhãn độc lập 20 ca, thống nhất quy tắc cho ca 8 và lập biện pháp phát hiện, khắc phục cho 5 ca đại diện. [Bảng lỗi](bang_loi.md) |
| D · Pilot | Chia ngẫu nhiên theo nhân viên, phân tầng theo depot, 20 người mỗi nhánh. Đối chứng chạy cùng thời gian. Kế hoạch có luật dừng về an toàn, chi phí và mức sử dụng. [Kế hoạch pilot](pilot_plan.yaml) |
| E · Gate 2a | Tính thử ba chỉ số, đặc tả event có `trace_id` và ghi rủi ro kinh tế. [Đặc tả chỉ số](chi_so.md) · [Hồ sơ launch v0](ho_so_launch_v0.md) |

## 4. Kết quả

- **Chi phí.** Ba phép thử A1 đều đạt. Chi phí mỗi việc thành công là **4.472 đ** và chi phí cả hệ thống là **5.865 đ/yêu cầu** sau khi tính phần nhân viên làm thay [simulated]. Với kịch bản xem lại 100%, chi phí trong phạm vi pilot tăng lên **12.516 đ/việc thành công** nếu mỗi ca làm lại mất 16,2 phút, bằng **1,04×** mức nhân viên tự làm [simulated].
- **Chỉ số và lỗi.** Trong đợt chạy thử, **82,83%** yêu cầu đóng trong 24 giờ và không mở lại trong 7 ngày, **27,12%** yêu cầu được xem lại có quyết định sửa hoặc bỏ gợi ý, và **4,25%** yêu cầu mở lại trong 7 ngày [simulated]. Hai bộ nhãn độc lập trùng **19/20 ca (95%)**.
- **Điều kiện pilot.** Xác nhận sổ cái trước khi báo đã hoàn, chống hoàn trùng, chấp nhận mức chênh tối thiểu phát hiện được là 6 điểm phần trăm, ghi đủ event để đo phút xem lại và làm lại, rồi giảm xem lại theo bậc khi đạt ngưỡng đã ghi trong hồ sơ.

## 5. Khó khăn và cách xử lý

Với 20 nhân viên mỗi nhánh và ICC 0,02, cỡ mẫu hiệu dụng có trần 1.000 mỗi nhánh, thấp hơn 1.251 cần để phát hiện chênh lệch 5 điểm phần trăm. Kế hoạch chọn mức 6 điểm phần trăm, cần 859 yêu cầu hiệu dụng mỗi nhánh, tương ứng ít nhất 299 yêu cầu mỗi nhân viên nếu cỡ cụm bằng nhau. Nếu tác động thực là 5 điểm phần trăm, power còn khoảng 0,64.

## 6. Tổng hợp đóng góp

- **Trần Anh Tú:** viết mã CP1–CP2, chạy phép thử A1 và xuất bảng độ nhạy.
- **Phạm Hữu Đức:** đối chiếu số chi phí và tiếp quản phần mã tính cỡ mẫu D1.
- **Nguyễn Thanh Liêm:** Người gắn nhãn 1, phụ trách bảng lỗi và đặc tả chỉ số, event.
- **Nguyễn Trung Anh:** Người gắn nhãn 2, kiêm giữ hồ sơ, phụ trách kế hoạch pilot và tổng hợp hồ sơ launch.

## 7. Hạn chế và hướng cải thiện

Đợt chạy thử chưa có đối chứng, nên các chỉ số hiện tại mô tả mẫu thử. Pilot cần đo thời gian xem lại và làm lại thực tế, kiểm tra lưu lượng yêu cầu đủ điều kiện theo từng nhân viên và chờ đủ cửa sổ 7 ngày trước khi chốt chỉ số.

## 8. Tài liệu tham khảo

[Đề bài Lab 13](../../docs/Ngay13_Lab13_De_bai_hoc_vien.docx) · [Dữ liệu và công thức](../../docs/du_lieu_va_cong_thuc.md) · [Tiêu chí chấm Gate 2a](../../RUBRIC.md).
