# Team

## Thông tin nhóm

- Tên nhóm: dimuon
- Lớp: L3A
- Repo nhóm: `K5-L3A-DAY13-dimuon-LaunchEconomics` (xem [SUBMISSION.md](SUBMISSION.md))
- URL repo, nhánh nộp, commit chốt: https://github.com/ducpahm03/K5-L3A-DAY13-dimuon-LaunchEconomics

## Thành viên và Phân công

| STT | Họ tên | MSSV | Email | GitHub | Vai trò chính | Nhiệm vụ cụ thể |
| --: | ------ | ---- | ----- | ------ | ------------- | --------------- |
|   1 | Trần Anh Tú | 2A202603368 | atus011205@gmail.com | atus011205 | **Người viết code** | Cài môi trường, code `src/lab13.py` (CP1, CP2), chạy các test A1 và xuất bảng độ nhạy |
|   2 | Phạm Hữu Đức | 2A202603380 | phamduc31103@gmail.com | ducpahm03 | **Người kiểm số** | Tính tay đối chiếu số liệu, điền `report/team/bang_chi_phi.md`, đổi viết code từ CP4 (D1) |
|   3 | Nguyễn Thanh Liêm | 2A202603358 | 26ai.liemnt@vinuni.edu.vn | Liemt0165 | **Người gắn nhãn 1** | Gắn nhãn độc lập 20 ca lỗi CP3, hoàn thiện `report/team/bang_loi.md` & `report/team/chi_so.md` |
|   4 |        |      |       |        | **Người gắn nhãn 2, kiêm giữ hồ sơ** | Gắn nhãn độc lập 20 ca lỗi CP3, hoàn thiện `report/team/pilot_plan.yaml` & `report/team/ho_so_launch_v0.md` |

### Bốn vai của lab:

- **Người viết code:** viết và chạy `src/lab13.py`.
- **Người kiểm số:** tính tay một con số để đối chiếu, điền bảng.
- **Người gắn nhãn 1:** đọc đề, theo dõi điều kiện "Xong khi"; gắn nhãn 20 ca độc lập ở CP3; đặc tả chỉ số và event.
- **Người gắn nhãn 2, kiêm giữ hồ sơ:** điền `report/team/ho_so_launch_v0.md` từ đầu buổi; gắn nhãn 20 ca độc lập ở CP3; hoàn thiện kế hoạch pilot.

*Lưu ý: Đổi người viết code sau giờ giải lao (Thành viên 2 tiếp quản code CP4), để ít nhất hai người trong nhóm tự tay tính được chi phí.*

## Cá nhân

Mỗi thành viên đồng thời tạo một báo cáo riêng trong `report/team/` theo dạng:

```text
report/team/MSSV_HoTen.md
```

Ví dụ: `report/team/2A202603380_PhamHuuDuc.md`.

## NguyenThanhLiem-2A202603358

### Phần việc phụ trách

- Nhiệm vụ C (Checkpoint 3): Độc lập gắn nhãn 20 ca lỗi theo 5 phân loại Google PAIR, tính tỷ lệ đồng thuận, thống nhất nhãn và xây dựng phương án khắc phục cho 5 ca tiêu biểu.
- Nhiệm vụ E: Phối hợp đặc tả các chỉ số đo lường, rủi ro kinh tế và cấu trúc danh sách event có `trace_id` trong `chi_so.md`.
- Đóng vai trò giám sát các điều kiện nghiệm thu ("Xong khi") và tiêu chuẩn rubric trên toàn bộ hồ sơ (nhãn `simulated`, cấu trúc luật dừng NẾU-TRONG-THÌ-KHÔNG THÌ, loại bỏ từ "production").

### Đóng góp cụ thể

- Hoàn thành bộ nhãn độc lập 20 ca lỗi trong `report/team/bang_loi.md`, đạt độ đồng thuận 85,0% (17/20 ca) với Người gắn nhãn 2.
- Thống nhất nguyên tắc phân loại cho 3 ca không trùng (Ca 6, Ca 8, Ca 13) dựa trên nguyên nhân gốc.
- Đề xuất phương án phát hiện định lượng (event, ngưỡng cảnh báo, tần suất) và phân công vai trò chịu trách nhiệm cho 5 ca lỗi đại diện.
- Rà soát tính nhất quán số liệu và tiêu chuẩn Gate 2a trong `ho_so_launch_v0.md` và `pilot_plan.yaml`.

### Bằng chứng

- File [report/team/bang_loi.md](report/team/bang_loi.md): Cột `Nhãn người 1`, quy tắc phân biệt cho 3 ca lệch và bảng khắc phục 5 ca.
- File [report/team/chi_so.md](report/team/chi_so.md): Cấu trúc 10 event có `trace_id` và các chỉ số đo lường.
- File báo cáo cá nhân [report/team/2A202603358_NguyenThanhLiem.md](report/team/2A202603358_NguyenThanhLiem.md).
