# Báo cáo cá nhân — NguyenThanhLiem-2A202603358

## 1. Thông tin thành viên

- Họ tên: Nguyễn Thanh Liêm
- MSSV: 2A202603358
- Email: 26ai.liemnt@vinuni.edu.vn
- GitHub: Liemt0165
- Vai trong nhóm: **Người gắn nhãn 1**

## 2. Phần việc phụ trách

- **Nhiệm vụ C (Checkpoint 3 — Bảng lỗi và cách khắc phục):**
  - Độc lập phân loại 20 ca lỗi của trợ lý hoàn phí LogiX-VN theo 5 phân nhóm lỗi của Google PAIR (*Do người dùng, Hệ thống, Ngữ cảnh, Giới hạn hệ thống, Ngầm*).
  - Đối chiếu với Người gắn nhãn 2, tính toán tỷ lệ đồng thuận trong nhóm (đạt yêu cầu $\ge 80\%$).
  - Phân tích nguyên nhân gốc cho các ca lệch nhãn và xây dựng quy tắc phân biệt.
  - Xây dựng bảng khắc phục cho 5 ca lỗi tiêu biểu với cơ chế phát hiện định lượng đo được và gán vai trò chịu trách nhiệm cụ thể.
- **Nhiệm vụ E (Checkpoint 5 — Chỉ số & Rủi ro):**
  - Phối hợp đặc tả danh mục 10 sự kiện (event) có gắn `trace_id` để đo lường vận hành.
  - Rà soát các chỉ số chính, chỉ số sử dụng, chỉ số an toàn và rủi ro kinh tế trong `chi_so.md`.
- **Giám sát điều kiện nghiệm thu ("Xong khi"):**
  - Kiểm tra việc gắn nhãn `simulated` cho toàn bộ số liệu giả lập trong các báo cáo.
  - Đảm bảo loại bỏ hoàn toàn thuật ngữ "production" trong hồ sơ theo chuẩn Gate 2a.
  - Kiểm tra cấu trúc 4 vế của các luật dừng trong `pilot_plan.yaml`.

## 3. Đóng góp cụ thể

1. **Phân loại lỗi độc lập và đối soát (Nhiệm vụ C):**
   - Hoàn thành bộ 20 nhãn độc lập trong 8 phút đúng nguyên tắc không trao đổi trước. Kết quả đối chiếu với Người gắn nhãn 2 đạt tỷ lệ đồng thuận **85,0% (17/20 ca)**, vượt ngưỡng chuẩn 80%.
   - Đưa ra giải thích nguyên nhân gốc để thống nhất 3 ca không trùng:
     - *Ca 6 (Do người dùng):* Khách chọn sai mục khi gửi yêu cầu; việc trợ lý thiếu gợi ý thuộc phần giải pháp khắc phục.
     - *Ca 8 (Hệ thống):* Dẫn sai điều khoản chính sách là lỗi sai lộ ra công khai, nhân viên bắt được, không phải lỗi ngầm.
     - *Ca 13 (Giới hạn hệ thống):* Bảo hiểm của đối tác là phạm vi ngoài chính sách hiện hành của LogiX-VN.
   - Hoàn thiện bảng khắc phục cho 5 ca đại diện (Ca 9, 7, 18, 4, 17) với event phát hiện cụ thể (`input_validation_failed`, đối soát tự động mỗi giờ, `handoff_to_staff`, kiểm tra mẫu 100 hồ sơ/tuần) và gán đúng các vai trò (PM trợ lý hoàn phí, Kỹ sư trưởng agent, Trưởng nhóm CSKH, Kế toán trưởng).
2. **Xây dựng danh mục Event và Chỉ số (Nhiệm vụ E):**
   - Đóng góp xây dựng cấu trúc 10 event có trường `trace_id` trong `chi_so.md` để thay thế số đo phút giả lập bằng dữ liệu thời gian thực trong giai đoạn pilot.
   - Tham gia rà soát hồ sơ launch v0 dài 1 trang và hỗ trợ thẩm định đề xuất "Go có điều kiện".
3. **Chuẩn bị và tham gia phản biện Gate 2a:**
   - Bảo vệ phân tích lỗi và đề xuất khắc phục trước hội đồng đánh giá.
   - Tham gia đánh giá chéo hồ sơ của nhóm khác và hoàn thiện `phieu_cham.md`.

## 4. Bằng chứng

- **File bảng lỗi:** `report/team/bang_loi.md` (cột "Nhãn người 1", quy tắc phân biệt và bảng khắc phục).
- **File chỉ số:** `report/team/chi_so.md` (mục 2 "Danh sách event cần ghi").
- **Hồ sơ launch:** `report/team/ho_so_launch_v0.md` (mục 5 "Bảng lỗi và cách khắc phục").
- **Nhánh Git & Commit:** Nhánh `NguyenThanhLiem-2A202603358`.

## 5. Công cụ AI đã dùng

- **Công cụ:** Antigravity (Gemini).
- **Mục đích sử dụng:**
  - Hỗ trợ tra cứu nhanh tài liệu Google PAIR (*Errors + Graceful Failure*) để hiểu sâu bản chất phân biệt giữa lỗi hệ thống (lộ ra) và lỗi ngầm (ẩn, chỉ lộ khi đối soát).
  - Soát lỗi logic trong các câu quy tắc phân biệt nguyên nhân gốc.
- **Tự kiểm tra:**
  - Trực tiếp đọc và phân tích từng ca lỗi từ đề bài gốc `Ngay13_Lab13_De_bai_hoc_vien.docx`.
  - Tự đối chiếu và biện luận từng trường hợp dễ gây nhầm lẫn để đảm bảo không bị AI "ảo giác" hay gán nhãn sai lệch.

## 6. Tự đánh giá

- Hoàn thành đầy đủ và đúng hạn trách nhiệm của vai trò Người gắn nhãn 1.
- Nắm chắc bản chất kinh tế học của agent và khung phân loại lỗi theo chuẩn Google PAIR.
- Phối hợp nhịp nhàng với Người gắn nhãn 2 và các thành viên trong nhóm để hồ sơ Gate 2a đạt độ chuẩn xác cao.
- **Đánh giá mức độ hoàn thành nhiệm vụ:** 100% / Xuất sắc.
