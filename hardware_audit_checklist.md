---

### 📄 File 3: `hardware_audit_checklist.md` (Biên bản đối chiếu phần cứng)

```markdown
# ⚡ BIÊN BẢN ĐỐI CHIẾU VÀ KIỂM TRA ĐẤU NỐI PHẦN CỨNG

**Mục tiêu:** Rà soát tủ điện thực tế so với sơ đồ nguyên lý.  
**Ngày thực hiện:** [Điền ngày]

### Bảng Kiểm Tra (Hardware Checklist)

| Hạng mục kiểm tra | Chân đấu nối (Sơ đồ) | Trạng thái | Đánh giá / Ghi chú |
| :--- | :--- | :---: | :--- |
| **Nguồn cấp mạch lực** | Q1 -> L1, L2, L3 (Driver) | 🟢 Đã đấu nối | Chắc chắn, có dùng domino chia nhánh |
| **Nguồn mạch điều khiển** | Q1 -> L1C, L2C (Driver) | 🟢 Đã đấu nối | Tách biệt an toàn với mạch lực |
| **Cấp nguồn Servo-ON** | Nguồn 24V -> Chân 1 (CN1) | ⚠️ Lưu ý | Cần đảm bảo có Jumper nối tắt từ Chân 1 sang Chân 25 và 49 để cấp điện trở nội. |
| **Tín hiệu băm xung** | Y0 (PLC) -> Chân 12 (PULS-) | 🟢 Đã kiểm tra | Đúng logic âm (dập mass). |
| **Tín hiệu đảo chiều** | Y1 (PLC) -> Chân 14 (SIGN-) | 🟢 Đã kiểm tra | Đúng logic âm (dập mass). |
| **Bypass an toàn** | Chân 10 (E-STOP) -> 0V/GND | 🟢 Đã nối tắt | Driver không báo lỗi E-STOP ảo. |
| **Khóa phanh từ (Brake)**| Y2 (PLC) -> Rơ-le -> BK+/BK- | 🟢 Đã đấu nối | Rơ-le trung gian hoạt động tốt, bảo vệ PLC. |

*Chú thích trạng thái:*
* 🟢: Passed / Hoạt động tốt
* ⚠️: Cần lưu ý / Needs Fix