# ĐIỀU KHIỂN VÀ GIÁM SÁT MÔ HÌNH XẾP HÀNG VÀO KHO (Automated Warehouse)

Đồ án môn học Trang bị điện - Khí nén | Trường Đại học Sư phạm Kỹ thuật TP. HCM (HCMUTE)

## 📖 Giới thiệu (Introduction)
Dự án mô phỏng và điều khiển một hệ thống xếp hàng vào kho tự động ở quy mô nhỏ. Hệ thống thực hiện các quy trình nhập hàng, lưu trữ và xuất hàng tự động hoặc bán tự động thông qua sự phối hợp giữa PLC Siemens S7-1200 và phần mềm mô phỏng nhà máy 3D Factory I/O. Giao diện giám sát được thiết kế trên HMI giúp người dùng dễ dàng theo dõi và điều khiển toàn bộ quá trình.

## ✨ Chức năng chính (Features)
Hệ thống hỗ trợ 3 chế độ vận hành linh hoạt:
- **Chế độ Tự động (Auto Mode):** Tự động tìm kiếm ô trống để nhập hàng (Load) và tìm kiếm kiện hàng để xuất kho (Unload) dựa trên thuật toán tối ưu.
- **Chế độ Thủ công (Manual Mode):** Cho phép người vận hành chỉ định tọa độ cụ thể của ô hàng (từ 1 đến 54) để thực hiện nhập hoặc xuất kiện hàng một cách chính xác.
- **Chế độ Chuyển tiếp (Bypass Mode):** Luân chuyển hàng hóa trực tiếp từ băng tải nhập sang băng tải xuất mà không cần lưu trữ vào kho.
- **Giám sát trực quan (HMI/SCADA):** Hiển thị trạng thái của 54 ô hàng (Trống/Có hàng) theo thời gian thực, số lượng hàng tồn kho (Inventory) và trạng thái các cơ cấu.

## 🛠 Cấu trúc dự án & Files
- `Automatic_warehouse.ap16`: File dự án điều khiển lập trình trên TIA Portal V16 (chứa mã nguồn cấu hình PLC và thiết kế giao diện HMI).
- `Automated Warehouse.factoryio`: File scene mô hình 3D của hệ thống kho hàng tự động để chạy trên phần mềm Factory I/O.
- `BC_CK_TBĐ_KN_NHOM13.pdf`: Báo cáo chi tiết đồ án (bao gồm tính toán chọn thiết bị, sơ đồ đấu dây, giải thuật và cấu trúc chương trình PLC).

## 💻 Yêu cầu hệ thống (Requirements)
### Phần mềm (Software)
- **TIA Portal V16** (hoặc phiên bản mới hơn)
- **Factory I/O** (khuyên dùng version 2.5.4)

### Phần cứng/Thiết bị mô phỏng (Simulated Hardware)
- **Bộ điều khiển chính:** PLC Siemens S7-1200 CPU 1214C DC/DC/DC (Mã thiết bị: 6ES7 214-1AG40-0XB0).
- **Màn hình giám sát:** HMI KTP900 Basic PN.
- **Cơ cấu chấp hành:** Các động cơ băng tải (nạp/xuất), cần cẩu Stacker Crane (trục X, Y, Z).
- **Hệ thống cảm biến:** Cảm biến quang phản xạ gương (nhận diện vị trí hàng), công tắc hành trình, Encoder.

## 🚀 Hướng dẫn cài đặt và sử dụng (Usage)
1. **Khởi động mô hình vật lý ảo (Factory I/O):** - Mở phần mềm Factory I/O và tải file `Automated Warehouse.factoryio`.
   - Đi đến `File > Drivers` và chọn cấu hình kết nối là `Siemens S7-PLCSIM` (nếu chạy mô phỏng) hoặc `Siemens S7-1200/1500` (nếu kết nối với PLC thật).
2. **Nạp chương trình điều khiển (TIA Portal):**
   - Mở file dự án `Automatic_warehouse.ap16` bằng TIA Portal V16.
   - Tiến hành Biên dịch (Compile) và Nạp (Download) chương trình xuống thiết bị PLC hoặc khởi động bộ mô phỏng PLCSIM.
   - Chạy mô phỏng màn hình HMI (Start simulation) để mở giao diện điều khiển.
3. **Vận hành hệ thống:**
   - Đảm bảo PLC đang ở trạng thái RUN.
   - Nhấn nút Play trên Factory I/O để hệ thống sẵn sàng hoạt động.
   - Trên màn hình HMI, sử dụng các công tắc chuyển để chọn chế độ làm việc (Auto/Manual/Bypass), thực hiện thao tác Load/Unload và theo dõi thông tin kho.

## 👥 Nhóm thực hiện (Contributors)
**Nhóm 13 - Lớp: EEQU333746_02**
- **Trần Nguyễn Thanh Lộc** (MSSV: 23151277)
- **Bùi Viết Tiến Dũng** (MSSV: 23151228)
- **Huỳnh Đăng Khoa** (MSSV: 23151263)
- **Nguyễn Vĩ Khang** (MSSV: 23151258)
- **Lê Khánh Hưng** (MSSV: 23151254)

*Giáo viên hướng dẫn:* Th.S. Trần Văn Sỹ

## 📌 Cảnh báo an toàn & Lưu ý (Note)
- Khi sử dụng chế độ **Manual**, bắt buộc người vận hành phải nhập tọa độ ô hàng (từ 1 đến 54) trước khi nhấn nút `MANUAL LOAD` hoặc `MANUAL UNLOAD`.
- Để chuyển đổi an toàn giữa các chế độ (ví dụ từ Bypass sang Auto/Manual), hệ thống yêu cầu phải tắt/chờ chu trình đang chạy kết thúc và các cơ cấu (càng nâng) đã thu về vị trí Home.
