# 📊 Data Storytelling: Thailand Household Income & Inequality

> **An Exploratory Data Analysis (EDA) and Statistical project evaluating income distribution and economic inequality across provinces and occupations in Thailand.** 
> *Developed as part of the Super AI Engineer Season 6 (Mini-Hackathon Level 1).*

---

## 🎯 Project Objective
To analyze and understand the structure of household income distribution in Thailand. The project focuses on identifying "Inequality Gaps" across geographic regions (provinces) and socio-economic classes using international statistical indices to reflect macroeconomic realities at a granular level.

---

## 📊 Data Source
Secondary aggregated data from the National Statistical Office (NSO) of Thailand.
* **Dataset:** `avg_income.csv` — Average monthly household income categorized by source of income and socio-economic class (2023).
* **Size:** 7,700 Records × 11 Columns

---

## 🛠️ Technical Skills Demonstrated
* **Programming:** Python (Pandas, NumPy)
* **Data Quality & Cleaning:** Missing Value Handling, String Manipulation (Stripping), Custom Dictionary Mapping, Outlier Treatment (Winsorization)
* **Statistical Analysis:** Gini Coefficient, Palma Ratio, Coefficient of Variation (CV), Income Disparity Ratio
* **Data Visualization:** Matplotlib, Seaborn (Histograms, KDE plots, Box plots, Bar charts with custom color palettes)

---

## 📂 Project Structure & Workflow

### 1️⃣ Data Quality Audit & Cleaning
* **Audit Trail:** Built an automated logging system to track data health (Timestamp, Null count, Outlier count).
* **Data Transformation:** Consolidated and mapped lengthy socio-economic class names into concise occupational groups (`occ1`, `occ2`).
* **Outlier Handling:** Addressed extreme values using **Winsorization** (IQR bounding) to preserve data distribution without dropping valuable records.

### 2️⃣ Exploratory Data Analysis (EDA)
* Analyzed the overall national income distribution compared to the mean and median.
* Conducted deep-dive Box Plot analyses to observe income density across primary and secondary occupational groups.
* Ranked the Top 5 highest-earning provinces and the Bottom 5 lowest-earning provinces.

### 3️⃣ Actionable Inequality Metrics (KPIs)
Implemented custom mathematical functions in Python to calculate and visualize inequality indicators:
* **Gini Coefficient:** Calculated the Gini index to rank the Top 10 provinces with the highest average income inequality.
* **Palma Ratio:** Segmented the data to compare the income share between the Top 10% and Bottom 40%.
* **Income Gap & Disparity Ratio:** Evaluated the average income ratio and absolute monetary gaps between different occupational groups.
* **Coefficient of Variation (CV):** Analyzed the income variance "within the same occupational group" to uncover hidden, within-group inequality.

---

## ⚠️ Methodological Note & Data Limitations
Because the dataset (`avg_income.csv`) consists of secondary, aggregated data without household-level population weights, the calculation of the Gini Coefficient and Palma Ratio in this project evaluates inequality based on **"group-level average income."** This approach highlights comparative trends across occupations and regions.

Therefore, these KPIs should not be directly compared to national inequality indices derived from individual-level microdata. In reality, hidden within-group inequality naturally results in a higher overall inequality ratio than what is captured through aggregated group averages.

---

## 🚀 How to Run the Code
1. You can view the full analysis directly in your browser by opening the Jupyter Notebook file: `Poomrat_mini_Hackathon_week_1.ipynb`.
2. To run and interact with the code, click the **"Open in Colab"** badge at the top of the notebook.
3. The dataset will be automatically downloaded within the first code cell via `wget`. No manual data upload is required.

---
*Created by Poomrat Thanapasee | Connect with me on [LinkedIn](https://www.linkedin.com/in/poomrat-thanapasee-6a99443b3/)*
