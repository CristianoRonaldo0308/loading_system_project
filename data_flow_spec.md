# 🔄 ĐẶC TẢ LUỒNG GIAO TIẾP HỆ THỐNG ĐĨA XOAY

Tài liệu mô tả chi tiết luồng truyền tải dữ liệu giữa các phân hệ: **Python (HMI) -> Rust (Engine) -> PLC (Hardware)**.

## Sơ Đồ Tổng Quan (Architecture Graph)

```mermaid
graph TD
    A[HMI Python - CustomTkinter] -->|JSON + Length Prefix qua TCP| B(Rust Backend Server - Port 5555)
    B -->|Tính toán động học| B
    B -->|Modbus RTU RS485 9600 8-N-1| C[PLC Delta DVP14SS2]
    C -->|High-speed Pulses Y0/Y1| D[Servo Driver CSD7]