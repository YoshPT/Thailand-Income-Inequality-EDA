# 📊 Data Storytelling: Thailand Household Income & Inequality

> **An exploratory data analysis (EDA) of household income and income gaps across provinces and occupations in Thailand.**
> *Developed as part of the Super AI Engineer Season 6 (Mini-Hackathon Level 1).*

---

## 🎯 Project Objective
To understand the structure of household income in Thailand and answer three questions:
1. **Who earns what?** Which occupations earn the most and the least, and how large is the gap?
2. **Where is the income gap?** Which provinces show the largest gaps between occupational groups?
3. **Where does income come from?** Which occupations depend on which income sources, and which are exposed to volatile income?

---

## 📊 Data Source
Secondary, aggregated data from the National Statistical Office (NSO) of Thailand.
* **Dataset:** `avg_income.csv` — average monthly household income by income source and socio-economic class, 2566 B.E. (2023).
* **Size:** 7,700 records × 11 columns = 77 provinces × 10 socio-economic classes × 10 income-source rows.
* **Unit:** Baht per month. Each value is a *group average* (province × occupational class), not a household record.

---

## 🛠️ Technical Skills Demonstrated
* **Programming:** Python (Pandas, NumPy)
* **Data quality & cleaning:** audit trail and cleaning log, missing-value handling, string cleaning, label mapping, consistency checks (components sum to totals)
* **Statistical analysis:** Gini coefficient, Palma ratio, coefficient of variation (CV), relative-to-mean income, income-share structure
* **Data visualization:** Matplotlib, Seaborn (histogram + KDE, box plots, grouped/stacked bar charts, scatter with quadrant annotations)

---

## 📂 Project Structure & Workflow

### 1️⃣ Data Quality Audit & Cleaning
* **Audit trail:** logs timestamp, row/column counts, nulls, duplicates, zero and negative values, and IQR outliers to a CSV.
* **Cleaning log** (rows removed / rows modified per step):

| Step | Action | Removed | Modified |
|---|---|---|---|
| 1 | Drop duplicates | 0 | 0 |
| 2 | Fill null `attribute` (a footnote column) with "ไม่มี" | 0 | 6,865 |
| 3 | Remove negative values (net farm profit < 0, and the totals that include it) | 36 | 0 |
| 4 | Sample-zero ("W" code: no sample in that cell) → `NaN`, not imputed | 0 | 812 |
| 5 | Flag IQR outliers in a separate column; **raw values are used in all analyses** | 0 | 0 |

* **Label mapping:** lengthy socio-economic class names mapped to concise groups (`occ1`, `occ2`).
* **Consistency checks:** total income equals the sum of its components (within 2 baht); one row per province × occupation.

### 2️⃣ Exploratory Data Analysis (EDA)
* Overall income distribution against the mean and median (histogram + KDE).
* Box plots by primary (`occ1`) and secondary (`occ2`) occupational groups.
* Top 5 and bottom 5 provinces by average income; regular vs. total income by occupation.

### 3️⃣ Inequality KPIs
* **Gini coefficient** — overall, by occupation, and by province (ranked).
* **Palma ratio** — top 10% vs. bottom 40% of group-level incomes.
* **Relative-to-mean income** — each occupation versus the average.
* **Coefficient of variation (CV)** — variation within each primary occupation group.

### 4️⃣ Data Storytelling (3 questions)
* **Q1 — Who earns what?** One bar per occupation, grouped by occupation type, with the highest/lowest highlighted, median markers, and the gap inside each group.
* **Q2 — Where is the gap?** Average income vs. between-occupation Gini per province, with quadrant guidance (raise income vs. reduce the gap) and a ranked top 15.
* **Q3 — Where does income come from?** Stacked income-source shares per occupation, with the main source and the share coming from volatile sources (business/farm profit + irregular income).

---

## 🔎 Key Findings
* **Occupation gap:** managers/professionals earn about **48.3K** baht/month vs. about **15.8K** for agricultural laborers — roughly **3.1×**.
* **Between-group inequality is moderate:** Gini ≈ **0.26** across all province × occupation groups; farmers are the highest by occupation (≈ 0.30).
* **Top province needs a caveat:** Chanthaburi ranks first on Gini (≈ 0.40) mainly because one group (tenant farmers, ≈ 181K baht/month) is far above the rest and may reflect a small sample.
* **Income structure:** employees get roughly **67–78%** of income from wages; farmers, fishers and the self-employed get roughly **66–75%** from business/farm profit, which is volatile and can turn negative.
* **Transfers are small:** government/other transfers are only about **5–7%** of income in every group.

---

## ⚠️ Methodological Notes & Data Limitations
* The dataset holds **group averages without household counts or population weights**. The Gini and Palma figures therefore measure the **gap between groups (province × occupation), unweighted** — not household-level inequality.
* They are **not comparable** with official national indices built from microdata (Thailand's official income Gini is roughly 0.4+). Hidden within-group inequality would make the true figures higher.
* The **Palma ratio is about 0.91**, i.e. below 1, because averaging compresses the income range. Do not read it as "the top 10% earn less than the bottom 40%".
* **Q2 measures the spread between occupations inside a province**, not inequality among households inside it.
* Province-level Gini rests on only 7–10 groups per province and is sensitive to small samples.
* **Negative values (36 rows) were removed**, so the farm profit of groups that made a loss is not counted. This changes the Q3 income shares by at most about 0.2 percentage points.
* Province-level means are **unweighted** averages across provinces.

---

## 🚀 How to Run the Code
1. Open `<your_notebook_name>.ipynb` in Google Colab (upload it, or open it from GitHub via Colab).
2. Run the cells **in order from the top**. The cleaning cell (Section 3) must run before the analysis cells.
3. The first code cell downloads the dataset (`avg_income.csv`) and the Thai font with `wget`, so no manual upload is needed. If the dataset link has expired, place `avg_income.csv` in the working directory and skip the `wget` line.

---
*Created by Poomrat Thanapasee | Connect with me on [LinkedIn](https://www.linkedin.com/in/poomrat-thanapasee-6a99443b3/)*
