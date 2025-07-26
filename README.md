# 🔌 Single-Phase Fully Controlled Rectifier using TCA785

> **Tiny in size, but Penny in value.**  
> Hi, I’m Penny — the guy who names things softly but designs them like they’re going into orbit 🚀  
> Welcome to my project – where high voltage meets high precision.

---

## 🧠 Project Overview

This repository contains the design and explanation of a **single-phase fully controlled rectifier** using:

- **TCA785** phase control IC
- **Thyristors (TYN1225)**
- **Opto-isolators (MOC3020)**

The system allows control of the **DC output voltage from 0V to nearly 220VDC** by adjusting the firing angle (**α**) of the thyristors.

> ⚠️ **High Voltage Warning:**  
> This circuit operates at 220VAC. Use proper **isolation**, **protective gear**, and **common sense**. Penny isn’t responsible if you turn into a resistor.

---

## ⚙️ Working Principle (EN)

Once powered on, the TCA785 starts its internal operation, consisting of:

- Phase detection
- Sawtooth ramp generation
- Comparator
- Pulse shaping and output stage

A control voltage (0–11V) is applied to **pin 11** of the TCA785. This is compared with a ramp signal at **pin 10**. When the ramp exceeds the control voltage, output pulses are generated at **pins 14 and 15**, corresponding to the desired firing angle (**0° to 180°**).

These pulses are:

- Sent through **optocouplers (MOC3020)** for electrical isolation
- Trigger four **SCRs (TYN1225)** in a full-bridge configuration

### 🔁 Load-side operation:

- **Positive half-cycle:**
  - IN2 is positive, IN1 is negative
  - **T1** and **T2** are triggered
  - Current path: `IN2 → T1 → Load → T2 → IN1`

- **Negative half-cycle:**
  - IN1 is positive, IN2 is negative
  - **T3** and **T4** are triggered
  - Current path: `IN1 → T3 → Load → T4 → IN2`

✅ This results in **unidirectional DC output** controllable from 0V to ~220V depending on α.

---

## Nguyên lý hoạt động (VN)

Mạch sử dụng IC **TCA785** để điều khiển góc kích SCR (Thyristor) thông qua điện áp điều khiển 0–11V. Khi điện áp này được đưa vào **chân 11**, nó sẽ được so sánh với sóng răng cưa tại **chân 10**, từ đó tạo xung kích trễ tại **chân 14 và 15**.

Các xung này:

- Qua opto MOC3020 để cách ly
- Điều khiển bốn thyristor T1 → T4 trong mạch chỉnh lưu cầu

### 🔁 Hoạt động mạch lực:

- **Bán kỳ dương:** IN2 dương, IN1 âm → T1 & T2 dẫn → Dòng: `IN2 → T1 → Tải → T2 → IN1`
- **Bán kỳ âm:** IN1 dương, IN2 âm → T3 & T4 dẫn → Dòng: `IN1 → T3 → Tải → T4 → IN2`

👉 Kết quả là dòng **một chiều qua tải**, có thể điều chỉnh được bằng góc kích α.

---

## 🛠️ How to Use

1. Connect the circuit to a **220VAC** source.
2. Apply a control voltage (0–11V) to **pin 11** (use a potentiometer or DAC).
3. Monitor output DC voltage across the load.
4. Adjust control voltage to modify the output (via firing angle delay).

---

## 🔧 Hardware Used

| Component | Value |
|----------|-------|
| TCA785 | Phase control IC |
| TYN1225 | SCR 1200V/25A |
| MOC3020 | Opto-isolator |
| Load | Resistive (ex: heater, lamp) |
| Control source | Potentiometer or DAC |

---

## 📂 Files Included

- `schematic.schdoc` – Altium schematic
- `pcb.pcbdoc` – Altium PCB layout
- `PDF/` – Rendered schematic & layout (for preview)
- `README.md` – This file

---

## ✨ Author Info

> 👤 **DUONG VAN THANG**  
> 🛠️ Embedded Developer | PCB Designer | Automation Enthusiast  
> 💡 *Tiny in size, but Penny in value.*

If you came here thinking I'm soft because of the name, I hope you stayed because of the sparks.

---

## 📬 Contact

- GitHub: [tinybutpenny](https://github.com/tinybutpenny)
- Email (personal): [duongthang090803@gmail.com](mailto:duongthang090803@gmail.com)


---

*Thanks for stopping by. Be safe. Measure twice, solder once.* 🔧
