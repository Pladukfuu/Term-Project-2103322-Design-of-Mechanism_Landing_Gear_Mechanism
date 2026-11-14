# Documentation
# Term-Project 2103-322 Design of Mechanism: Landing Gear Mechanism

เอกสารสรุปสาระสำคัญของรายงานฉบับสมบูรณ์สำหรับโปรเจกต์ออกแบบและวิเคราะห์กลไกพับล้อเครื่องบิน (Aircraft Landing Gear Mechanism) รายวิชา **2103-322 Design of Mechanism** ปีการศึกษา 2569 ภาควิชาวิศวกรรมเครื่องกล คณะวิศวกรรมศาสตร์ จุฬาลงกรณ์มหาวิทยาลัย

* **ผู้จัดทำ:** สรสิช ศรีวิเศษ (รหัสนิสิต 6730520521)

---
## 1. Document Directory 
* `Term project Landing gear mechanism.pdf` – เล่มรายงานฉบับสมบูรณ์ 
* `Term project Landing gear mechanism.docx` – เล่มรายงานฉบับสมบูรณ์ ครอบคลุมการเขียน Kinematic Diagram, การคำนวณ DoF, การจำลองใน Simscape Multibody และการวิเคราะห์ Kinematics ของจุดศูนย์กลางล้อ

---

## 2. Mechanism Overview & DoF Analysis (Part I)
กลไกพับล้อเครื่องบินออกแบบให้ทำงานเป็น **Motion Generator** เพื่อพาล้อเคลื่อนที่จากตำแหน่งกางสุด (Fully Extended) ไปยังตำแหน่งพับเก็บสุด (Fully Retracted) โดยมีรายละเอียดการวิเคราะห์ทางจลนศาสตร์ดังนี้:
* **Number of Links ($L$):** `10` ชิ้น (โดยให้ Link 1 เป็นโครงยึดติดกับลำตัวเครื่องบิน / Ground Link)
* **Kinematic Pairs:**
  * ($J_1$): `13` (ประกอบด้วย 12 Revolute Joints และ 1 Prismatic Joint บริเวณกระบอกสูบ)
  * ($J_2$): `0`
* **Degrees of Freedom (Grübler's Equation):**
  $$\text{DoF} = 3(L - 1) - 2J_1 - J_2 = 3(10 - 1) - 2(13) - 0 = 1$$

---

## 3. Simscape Multibody Setup (Part II)
* **Actuation Input:** ป้อนสัญญาณขับเคลื่อน (1-DoF Input) ที่บริเวณ **Purple Link**
* **Sensors & Data Acquisition:**
  * **Input Revolute Joint:** วัดมุมขับเคลื่อน (`theta_input`) และแรงบิด (`Torque_input`)
  * **Piston Prismatic Joint:** วัดระยะชัก ความเร็ว และความเร่งของกระบอกลูกสูบ (`x`, `v`, `a`)
  * **Wheel Center (`Transform Sensor`):** วัดตำแหน่ง ความเร็ว และความเร่งเชิงเส้นเทียบกับ World Frame (`x_wheel`, `v_wheel`, `a_wheel`)

---

## 4. Kinematic Analysis Summary (Wheel Center)
ผลการจำลองการเคลื่อนที่ช่วงพับเก็บล้อ ($t = 0\text{ s}$ ถึง $4.4\text{ s}$):
* **Position & Trajectory (Y-Z Plane):** จุดศูนย์กลางล้อเคลื่อนที่เป็นเส้นโค้งราบรื่น (Smooth Curve) โดยไม่มีจุดหักมุมชั่วขณะ
* **Velocity ($v$):** เริ่มต้นที่ `25.0 mm/s` ลดลงต่ำสุดที่ `18.7 mm/s` (ณ $t = 3.6\text{ s}$) และเพิ่มขึ้นสู่ค่าสูงสุดที่ **`34.0 mm/s`** ณ ช่วงท้ายตอนพับสุด ($t = 4.4\text{ s}$)
* **Acceleration ($a$):** คงที่สม่ำเสมอช่วงประมาณ `10 mm/s²` ก่อนเพิ่มขึ้นเป็น **`135.0 mm/s²`** ณ ช่วงปลายการกวาด ($t = 4.4\text{ s}$) เนื่องจากผลของความไม่เป็นเส้นตรงของกลไก (Linkage Nonlinearity)
