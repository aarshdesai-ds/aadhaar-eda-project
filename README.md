# 🆔 Aadhaar Scheme Impact Analysis (State of Aadhaar 2019)

This project explores the real-world impact of Aadhaar — India's biometric identity system — using in-depth survey data from the **State of Aadhaar 2019**. Through structured analysis, we examine Aadhaar's accessibility, usage, perception, and inclusivity across demographics and regions.

---

## 📦 Dataset Overview

**Source**: [State of Aadhaar Official Website](https://stateofaadhaar.in/download-reports.php)  
**Files Used**:
- `20191118-over-sample-hh.csv`
- `20191118-over-sample-mem.csv`
- `20191118-random-sample-hh.csv`
- `20191118-random-sample-mem.csv`

Each file represents household- and individual-level survey data with responses on Aadhaar usage, demographics, public service access, and more.

---

## 🧠 Objectives

The project answers the following key questions:

1. How many Aadhaar centres exist in urban and rural India? Does this affect enrolment?
2. Has Aadhaar changed implementation of services like bank accounts and SIM registration?
3. What is Aadhaar’s impact on school admissions?
4. How accessible is Aadhaar to vulnerable groups (e.g., migrant workers, third gender)?
5. What are people's sentiments about Aadhaar?

---

## 📊 Analysis Pipeline

### 📌 1. Data Loading & Filtering
- Combined oversample and random sample datasets
- Selected relevant columns for analysis (region, gender, Aadhaar possession, services)

### 📈 2. Demographic Analysis
- State-wise distribution of participants
- Urban vs rural representation
- Gender and religion representation
- **Conclusion**: Sample is biased toward certain states and religions

### 🏛️ 3. Aadhaar Centre Coverage
- Counted Aadhaar PSUs in rural vs urban areas
- Compared PSU count with enrolment numbers
- **Insight**: More centres → higher enrolment

### 💼 4. Government Services Access
- Analyzed Aadhaar use in:
  - Bank account openings
  - SIM card purchases
- **Insight**: Aadhaar simplifies access and is widely used for verification

### 🏫 5. School Admission Barriers
- Checked if Aadhaar was mandatory for admission
- Counted denials due to Aadhaar absence
- **Insight**: Aadhaar was wrongly enforced as mandatory in some schools

### 🧍‍♂️ 6. Accessibility for Vulnerable Groups
- Migrant labourers, elderly, homeless, third gender
- **Insight**: These groups have **significantly lower Aadhaar access**

### 🗣️ 7. Sentiment Analysis
- Evaluated:
  - Perceived impact on household
  - Satisfaction with Aadhaar
  - Life improvement/worsening due to Aadhaar
- **Result**: Majority satisfied and view Aadhaar as beneficial

---

## 📌 Conclusions

- 📉 **Data bias** exists by region and religion
- 🏢 **More Aadhaar centres** directly increase enrolment
- 🏫 **School access** was sometimes wrongly denied due to missing Aadhaar
- 📱 **Bank and telecom** services heavily rely on Aadhaar
- 🚫 **Vulnerable groups are underserved** in Aadhaar coverage
- ✅ **Public sentiment is mostly positive**

---

## 💡 Recommendations

1. **Increase Aadhaar centres**, especially in underserved rural areas
2. **Enforce Supreme Court rulings** to prevent Aadhaar-based service denial
3. **Conduct outreach** for migrant workers, elderly, homeless, and third gender groups
4. **Promote Aadhaar** as a standard ID while safeguarding privacy

---

## 🧰 Tech Stack

- Python 3
- Pandas, NumPy (data wrangling)
- Matplotlib, Seaborn (visualizations)
- Jupyter Notebook

---

## 🚀 How to Run

1. Clone the repository  
`git clone https://github.com/aarshdesai-ds/aadhaar-eda-project.git`

2. Launch the notebook
 `jupyter notebook aadhaar-eda-project.ipynb`

3. Run all cells to reproduce the visualizations and statistical outputs
