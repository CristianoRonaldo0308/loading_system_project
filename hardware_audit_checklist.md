# ⚡ BIÊN BẢN ĐỐI CHIẾU VÀ KIỂM TRA ĐẤU NỐI PHẦN CỨNG

**Mục tiêu:** Rà soát tủ điện thực tế so với sơ đồ nguyên lý phần cứng[cite: 4].
**Ngày thực hiện:** 21/07/2026
**Người kiểm tra:** Vũ Thành Đạt

### Bảng Kiểm Tra (Hardware Checklist)

| Hạng mục kiểm tra | Chân đấu nối vật lý | Trạng thái | Đánh giá / Ghi chú |
| :--- | :--- | :---: | :--- |
| **Nguồn cấp PLC Delta** | Nguồn 24VDC -> Chân `UP` (+24V) và `ZP` (0V) | 🟢 Đã đấu nối | Cấp nguồn cho ngõ ra Transistor NPN của PLC[cite: 4]. |
| **Nguồn cấp mạch lực** | Q1 -> L1, L2, L3 (Driver CSD7) | 🟢 Đã đấu nối | Chắc chắn, có dùng domino chia nhánh. |
| **Nguồn mạch điều khiển** | Q1 -> L1C, L2C (Driver CSD7) | 🟢 Đã đấu nối | Tách biệt an toàn với mạch lực. |
| **Jumper nguồn nội Driver**| Nguồn 24V -> Chân 1, 25 (`SIGN+`), 49 (`PULS+`) | ⚠️ Lưu ý | Cần đảm bảo nối tắt Jumper trong cổng DB50 để cấp điện trở hạn dòng nội 2kΩ[cite: 4]. |
| **Tín hiệu băm xung** | `Y0` (PLC) -> Chân 12 (`PULS-`) | 🟢 Đã kiểm tra | Đúng chuẩn ngõ ra Transistor NPN dập mass tạo xung vuông[cite: 4]. |
| **Tín hiệu đảo chiều** | `Y1` (PLC) -> Chân 14 (`SIGN-`) | 🟢 Đã kiểm tra | Y1 = OFF (Quay Phải), Y1 = ON (Quay Trái)[cite: 4]. |
| **Tín hiệu Servo-ON** | `Y5` (PLC) -> Chân 3 (`SV-ON`) | 🟢 Đã kiểm tra | Khi PLC RUN, Y5 dập mass để khóa cứng cốt Servo[cite: 4]. |
| **Truyền thông RS485** | `D+`/`D-` (COM2 PLC) -> `D+`/`D-` (USB-RS485) | 🟢 Đã kiểm tra | Đã đấu đúng cực, cáp xoắn tốt, đảm bảo truyền thông Modbus RTU ổn định[cite: 4]. |
| **Bypass an toàn** | Chân 10 (E-STOP) -> 0V/GND | 🟢 Đã nối tắt | Hàn chụm xuống GND để bypass E-STOP ảo trong pha thử nghiệm bàn máy[cite: 4]. |
| **Kết nối Motor** | Cổng CN2 và cáp U, V, W -> Servo Motor | 🟢 Đã đấu nối | Cáp Encoder 17-bit cắm chặt, Driver không báo lỗi E.xxx[cite: 4]. |

---
### *Chú thích trạng thái:*
* 🟢 **Passed:** Đã đấu nối đúng và hoạt động tốt.
* ⚠️ **Needs Check:** Đã đấu nối nhưng cần lưu ý kỹ thuật đặc biệt.
* 🔴 **Action Required:** Lỗi, đấu nối sai hoặc chưa thực hiện.