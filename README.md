# 🇹🇭 Data Storytelling: Thailand Household Income & Inequality

> **An Exploratory Data Analysis (EDA) and Statistical project evaluating income distribution and economic inequality across provinces and occupations in Thailand.** 
> *Developed as part of the Super AI Engineer Season 6 (Mini-Hackathon Level 1).*

---

## 🎯 Project Objective
เพื่อวิเคราะห์และทำความเข้าใจโครงสร้างการกระจายตัวของรายได้ครัวเรือนไทย โดยมุ่งเน้นการค้นหา "ช่องว่างความเหลื่อมล้ำ" (Inequality Gap) เชิงพื้นที่ (จังหวัด) และเชิงอาชีพ ผ่านการใช้ดัชนีชี้วัดทางสถิติระดับสากล เพื่อสะท้อนภาพรวมของเศรษฐกิจระดับจุลภาค

---

## 📊 Data Source
ข้อมูลทุติยภูมิ (Secondary Data) แบบสรุปค่าเฉลี่ย (Aggregated Data) จากสำนักงานสถิติแห่งชาติ (NSO) 
* **Dataset:** `avg_income.csv` — รายได้เฉลี่ยต่อเดือนของครัวเรือน จำแนกตามแหล่งที่มาของรายได้ และสถานะทางเศรษฐสังคมของครัวเรือน ปี 2566
* **Size:** 7,700 Records × 11 Columns

---

## 🛠️ Technical Skills Demonstrated
* **Programming:** Python (Pandas, NumPy)
* **Data Quality & Cleaning:** Missing Value Handling, Text Striping, Custom Dictionary Mapping, Outlier Treatment (Winsorization)
* **Statistical Analysis:** Gini Coefficient, Palma Ratio, Coefficient of Variation (CV), Disparity Ratio
* **Data Visualization:** Matplotlib, Seaborn (Histograms, KDE plots, Box plots, Bar charts with custom palettes)

---

## 📂 Project Structure & Workflow

### 1️⃣ Data Quality Audit & Cleaning
* **Audit Trail:** สร้างระบบ Log บันทึกประวัติสุขภาพข้อมูลอัตโนมัติ (Timestamp, Null count, Outlier count)
* **Data Transformation:** ยุบรวมและเปลี่ยนชื่อกลุ่มสถานะทางเศรษฐสังคม (Socio-economic class) ที่ยาวและซับซ้อนให้เป็นกลุ่มอาชีพที่กระชับ (`occ1`, `occ2`)
* **Outlier Handling:** จัดการค่าที่ผิดปกติสุดโต่งด้วยเทคนิค **Winsorization** (การจำกัดขอบเขต IQR) เพื่อรักษาสภาพการกระจายตัวของข้อมูลโดยไม่ต้องลบข้อมูลทิ้ง

### 2️⃣ Exploratory Data Analysis (EDA)
* วิเคราะห์การกระจายตัวของรายได้รวมทั้งประเทศเทียบกับค่าเฉลี่ยและมัธยฐาน
* เจาะลึกรายได้เฉลี่ยแบบ Box Plot เพื่อดูความหนาแน่นของฐานรายได้ในแต่ละกลุ่มอาชีพหลักและอาชีพย่อย
* จัดอันดับ Top 5 จังหวัดที่มีรายได้สูงสุด และ Bottom 5 จังหวัดรั้งท้าย

### 3️⃣ Actionable Inequality Metrics (KPIs)
ใช้ฟังก์ชันทางคณิตศาสตร์แบบ Custom ใน Python เพื่อคำนวณและสร้างกราฟชี้วัดความเหลื่อมล้ำ:
* **Gini Coefficient:** คำนวณสัมประสิทธิ์จีนีเพื่อจัดอันดับ Top 10 จังหวัดที่มีความเหลื่อมล้ำของค่าเฉลี่ยสูงสุด
* **Palma Ratio:** แบ่งกลุ่มข้อมูลเพื่อเปรียบเทียบสัดส่วนรายได้ระหว่าง Top 10% และ Bottom 40%
* **Income Gap & Disparity Ratio:** เปรียบเทียบอัตราส่วนรายได้เฉลี่ยระหว่างกลุ่มอาชีพ
* **Coefficient of Variation (CV):** วิเคราะห์ความแปรผันของรายได้ "ภายในกลุ่มอาชีพเดียวกัน" เพื่อหาความเหลื่อมล้ำแฝง

---

## ⚠️ Methodological Note & Data Limitations
เนื่องจากชุดข้อมูล `avg_income.csv` เป็นข้อมูลทุติยภูมิที่ผ่านการสังเคราะห์และสรุปผลในระดับมหภาค (Aggregated Data) โดยไม่มีตัวแปรน้ำหนักประชากร (Population Weight) การคำนวณค่าสัมประสิทธิ์จีนี (Gini Coefficient) และสัดส่วนปาลมา (Palma Ratio) ในโปรเจกต์นี้ จึงเป็นการประเมินบนฐานของ **"ค่าเฉลี่ยรายได้ระดับกลุ่ม"** เพื่อสะท้อนแนวโน้มเชิงเปรียบเทียบข้ามกลุ่มอาชีพและภูมิภาคเป็นหลัก 

ค่า KPI ดังกล่าวจึงไม่สามารถนำไปเทียบเคียงกับดัชนีความเหลื่อมล้ำที่คำนวณจากข้อมูลดิบรายบุคคล (Microdata) ได้โดยตรง เนื่องจากอาจมีความเหลื่อมล้ำแฝง (Within-group Inequality) ภายในแต่ละกลุ่มอาชีพ ซึ่งโดยธรรมชาติจะมีสัดส่วนความเหลื่อมล้ำที่สูงกว่าค่าเฉลี่ยระดับกลุ่มที่ปรากฏในชุดข้อมูล

---

## 🚀 How to Run the Code
1. You can view the full analysis directly in your browser by opening the Jupyter Notebook file: `Poomrat_mini_Hackathon_week_1.ipynb`.
2. To run and interact with the code, click the **"Open in Colab"** badge at the top of the notebook.
3. The dataset will be automatically downloaded within the first code cell via `wget`. No manual data upload is required.

---
*Created by [ชื่อของคุณ] | Connect with me on [LinkedIn URL]*
