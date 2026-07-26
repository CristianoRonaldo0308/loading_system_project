# 📝 BÁO CÁO CODE REVIEW: PHÂN HỆ RUST BACKEND & PLC

**Ngày thực hiện:** 20/07/2026  
**Người thực hiện:** [Tên của bạn]  
**Người đánh giá (Senior):** Anh Thạch

---

## 1. Đánh giá Cấu trúc (Architecture Review)

- [x] **Ưu điểm kiến trúc:** Khung code được tổ chức tốt theo mô hình 3 lớp. Việc tách biệt `modbus.rs` (giao tiếp vật lý) và `test_cases.rs` (kịch bản kiểm thử) giúp dễ bảo trì và mock data.
- [x] **Xử lý dữ liệu:** Xử lý tốt Word Swap 32-bit (dịch bit) cho thanh ghi D10-D11 của PLC.

## 2. Các Lỗi Nghiêm Trọng Cần Cải Thiện (Critical Bugs)

- [ ] 🔴 **[BUG-01] Sai cấu hình Modbus RTU:** 
  - **Vấn đề:** Code Rust (`modbus.rs`) đang cấu hình chuẩn `8-N-1` (8 Data bits, None Parity). Tuy nhiên, PLC Delta mặc định sử dụng `7-E-1`.
  - **Đề xuất fix:** Nạp Ladder cấu hình thanh ghi `D1120` ép PLC chạy chuẩn `8-N-1` để đồng bộ với Rust.
- [ ] 🔴 **[BUG-02] Sai địa chỉ thanh ghi D1343:** 
  - **Vấn đề:** Tại kịch bản Test Case 5, hệ thống gọi `plc.write_register(8535)`. Vùng nhớ D của Delta ánh xạ từ hệ cơ số `4096`. 
  - **Đề xuất fix:** Đổi địa chỉ D1343 thành `4096 + 1343 = 5439`. Tránh ghi vào `8535` gây lỗi Exception.
- [ ] 🟠 **[BUG-03] Mâu thuẫn thông số hộp số điện tử:** 
  - **Vấn đề:** Code Rust hardcode 360 độ = 120.000 xung. Tài liệu thiết kế lại ghi 360 độ = 1.000 xung. 
  - **Đề xuất fix:** Thống nhất lại tử số/mẫu số (Ft-3.05 và Ft-3.06) trên Servo Driver CSD7.
  