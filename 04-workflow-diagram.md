# VinFast Aftersales — Current-State Workflow

**Caption:** Current-state service intake (before fault codes): booking → workshop wait → advisor symptom/policy check (bottleneck) → technician OBD read → promised delivery time with late penalty.

```mermaid
flowchart LR
  A["1. Đặt lịch<br/>(App / tổng đài)"]
  B["2. Khách tới xưởng<br/>chờ cố vấn"]
  C["3. Cố vấn hỏi triệu chứng<br/>+ đối chiếu chính sách miệng<br/>⚠ BOTTLENECK"]
  D["4. Kỹ thuật viên<br/>cắm máy đọc mã lỗi"]
  E["5. Ghi giờ giao trên lệnh sửa<br/>Nếu trễ cam kết: 500.000đ/ngày"]

  A -->|"Handoff: App/tổng đài → xưởng"| B
  B --> C
  C -->|"Handoff: cố vấn → kỹ thuật viên"| D
  D --> E

  style C fill:#dc2626,stroke:#991b1b,color:#ffffff
  style A fill:#dbeafe,stroke:#1e40af,color:#0f172a
  style B fill:#dbeafe,stroke:#1e40af,color:#0f172a
  style D fill:#dbeafe,stroke:#1e40af,color:#0f172a
  style E fill:#dbeafe,stroke:#1e40af,color:#0f172a
```
