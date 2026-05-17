# Aadhaar Impact Analysis (State of Aadhaar 2019)

An exploratory data analysis of India's biometric identity system using survey data from the State of Aadhaar 2019 initiative, examining Aadhaar's accessibility, integration with public services, and impact across demographics and vulnerable populations.

---

## Table of Contents

- [Overview](#overview)
- [Research Questions](#research-questions)
- [Dataset Description](#dataset-description)
- [Key Findings](#key-findings)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [How to Run](#how-to-run)
- [Results Summary](#results-summary)
- [Ideas for Extension](#ideas-for-extension)

---

## Overview

This project analyzes 112,244 survey records across 4 data files from the State of Aadhaar 2019 in-depth survey, covering household- and individual-level responses from 28 Indian states. The analysis investigates whether Aadhaar — India's 12-digit biometric identity number — is equitably accessible, legally compliant in its enforcement, and broadly beneficial to the population it is meant to serve.

The core questions: Who has Aadhaar, who doesn't, and what does that gap cost them?

---

## Research Questions

- How does Aadhaar centre (PSU) density relate to enrolment rates in urban vs. rural India?
- Is Aadhaar genuinely integrated into banking and telecom services — or is it coercively enforced?
- Are schools illegally mandating Aadhaar for admission in violation of the Supreme Court ruling?
- Which vulnerable groups (migrant workers, homeless, elderly, third gender) are most excluded from Aadhaar coverage?
- What is the public's overall satisfaction with Aadhaar, and does it vary by demographic?

---

## Dataset Description

**Source**: [State of Aadhaar Official Survey (2019)](https://stateofaadhaar.in/)

### Survey Files (4 files)

| File | Type | Rows |
|---|---|---|
| `20191118_State of Aadhaar_in-depth survey_random_sample_hh.csv` | Household-level, random sample | 17,323 |
| `20191118_State of Aadhaar_in-depth survey_over_sample_hh.csv` | Household-level, oversample | 4,794 |
| `20191118_State of Aadhaar_in-depth survey_random_sample_mem.csv` | Individual-level, random sample | 73,014 |
| `20191118_State of Aadhaar_in-depth survey_over_sample_mem.csv` | Individual-level, oversample | 17,113 |
| **Total** | | **112,244** |

The household files capture residence, infrastructure, and household-level Aadhaar status. The member files capture individual demographics, Aadhaar possession, service usage, and sentiment.

### Key Column Groups

| Column Group | Description |
|---|---|
| Geography | State, district, urban/rural classification, settlement size |
| Demographics | Age, gender, religion, caste, occupation |
| Aadhaar Status | Whether member holds Aadhaar, reason for absence if not |
| Service Usage | Bank account, SIM card, school admission, PDS, MGNREGS |
| Centres (PSU) | Number of Aadhaar enrolment centres in area |
| Sentiment | Perceived household impact, satisfaction rating, life quality change |

---

## Key Findings

### 1. Dataset Has Significant Regional and Demographic Bias

The sample of ~2,000 analyzed participants is not nationally representative:

- **Most surveyed states**: Jharkhand (~255 participants), Bihar (218), Chhattisgarh (193)
- **Least surveyed states**: Karnataka (2), Kerala (9), Gujarat (5)
- Eastern and central India are heavily overrepresented; southern and western states are nearly absent
- **Gender split**: Male 55% (1,100), Female 38% (762), Third gender 7% (138)
- **Religion split**: Hindu 81% (1,631), Muslim 11% (216), Sikh 4% (74), Christian <1% (19)
- **Settlement type**: Urban small 690, Rural small 625, Urban large 482, Rural large 203 — skewed toward smaller settlements

### 2. Aadhaar Centre Density Directly Predicts Enrolment

| Area Type | Centres (PSUs) | Enrollments |
|---|---|---|
| Rural | 174 | 828 |
| Urban | 214 | 1,172 |

Urban areas have 23% more centres and 42% higher enrolment. The relationship is directional: enrolment scales with access. Rural expansion of Aadhaar PSUs would likely produce proportional gains in coverage.

### 3. Aadhaar is Widely Used for Banking and Telecom

- **Bank account opening**: 832 respondents used Aadhaar; 456 did not
- **SIM card purchase**: 770 respondents used Aadhaar as primary ID; 331 used alternative documents
- Aadhaar has become the de facto KYC document in both banking and telecom sectors, used by ~65% of surveyed individuals for each service type

### 4. Schools Are Illegally Mandating Aadhaar for Admission

Despite the Supreme Court ruling that Aadhaar cannot be mandated for school admission:

| Situation | Count |
|---|---|
| Aadhaar was mandatory for admission | 230 |
| No alternative ID was accepted | 75 |
| Aadhaar was optional | 67 |
| Respondent did not know | 42 |
| **Denied services due to missing Aadhaar** | **47** |

47 individuals were denied services — including mid-day meals — solely because they lacked Aadhaar. This represents a direct legal violation with measurable human cost.

### 5. Vulnerable Populations Are Severely Underserved

Overall Aadhaar possession in the analysis sample: 1,782 with Aadhaar, 200 without, 4 unsure (~89% coverage rate at the aggregate).

But disaggregating by vulnerable group reveals severe exclusion:

| Population Group | Aadhaar Coverage (per 1,000) |
|---|---|
| General population (approx.) | ~890 / 1,000 |
| Elderly | 222 / 1,000 |
| Homeless | 77 / 1,000 |
| Migrant labourers | 23 / 1,000 |
| Third gender | 0 / 1,000 (no recorded holders) |

Migrant labourers have a 2.3% coverage rate — 39x lower than the general sample rate. Third gender individuals recorded zero Aadhaar holders in the sample, reflecting both social exclusion and data infrastructure failures.

### 6. Public Sentiment is Strongly Positive Despite Real Barriers

| Sentiment Measure | Result |
|---|---|
| "Affects us a lot" | 753 (43%) |
| "Affects us a little" | 622 (36%) |
| "Doesn't affect us" | 463 (27%) |
| Satisfied with Aadhaar | 1,422 / 1,620 (87.8%) |
| Unsatisfied | 80 / 1,620 (4.9%) |
| Life improved due to Aadhaar | 1,377 / 1,880 (73.2%) |
| No change | 472 / 1,880 (25.1%) |
| Life worsened | 31 / 1,880 (1.6%) |

~74% of respondents feel Aadhaar has impacted their household; ~87.8% are satisfied; ~73% report life improvement. Positive sentiment coexists with documented exclusion — indicating that those who have Aadhaar largely benefit from it, while those without face barriers that don't register in aggregate satisfaction scores.

---

## Project Structure

```
aadhaar-eda-project/
│
├── aadhaar-eda-project.ipynb    # Main analysis notebook
├── README.md
│
└── data/                        # Survey data files
    ├── 20191118_State of Aadhaar_in-depth survey_random_sample_hh.csv
    ├── 20191118_State of Aadhaar_in-depth survey_over_sample_hh.csv
    ├── 20191118_State of Aadhaar_in-depth survey_random_sample_mem.csv
    └── 20191118_State of Aadhaar_in-depth survey_over_sample_mem.csv
```

---

## Requirements

```
Python 3.8+
pandas
numpy
matplotlib
seaborn
jupyter
```

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

---

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/aarshdesai-ds/aadhaar-eda-project.git
cd aadhaar-eda-project
```

2. Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

3. Launch Jupyter:

```bash
jupyter notebook aadhaar-eda-project.ipynb
```

4. Run all cells sequentially (`Cell > Run All`).

---

## Results Summary

| Analysis Area | Key Metric | Finding |
|---|---|---|
| Dataset scope | 112,244 survey records across 4 files | Not nationally representative |
| Regional coverage | 28 states surveyed | Jharkhand, Bihar, Chhattisgarh dominate |
| Gender breakdown | Male 55%, Female 38%, Third gender 7% | Male-skewed sample |
| Aadhaar centres | 174 rural, 214 urban | Urban areas have 23% more centres |
| Enrolment by area | 828 rural, 1,172 urban | Correlates directly with centre count |
| Banking integration | 832 / 1,288 used Aadhaar for bank account | ~65% usage rate |
| Telecom integration | 770 / 1,101 used Aadhaar for SIM | ~70% usage rate |
| School Aadhaar denial | 47 individuals denied services | Legal violation documented |
| Migrant worker coverage | 23 / 1,000 have Aadhaar | 2.3% — severely excluded |
| Elderly coverage | 222 / 1,000 have Aadhaar | 22.2% — largely excluded |
| Homeless coverage | 77 / 1,000 have Aadhaar | 7.7% — largely excluded |
| Third gender coverage | 0 / 1,000 have Aadhaar | Systemic exclusion |
| Overall satisfaction | 1,422 / 1,620 satisfied | 87.8% approval rate |
| Life improvement | 1,377 / 1,880 report improvement | 73.2% positive impact |

---

## Ideas for Extension

### 1. State-Level Coverage Regression
The dataset is geographically imbalanced but covers enough states to run a regression of Aadhaar possession rate on state-level centre density, rural/urban split, and literacy rate. This would quantify how much of the coverage gap is infrastructure-driven vs. demand-side.

### 2. Quantifying the Denial Cost
47 individuals were denied services due to missing Aadhaar. Connecting denial rates to vulnerable group membership (migrant workers, homeless, elderly) would reveal whether denials cluster in the most excluded groups — and estimate the total affected population if extrapolated to the full 112,244 records.

### 3. Sentiment vs. Demographic Subgroup Analysis
Aggregate satisfaction is 87.8%, but this likely masks variation. Stratifying sentiment scores by state, religion, gender, and urban/rural classification would reveal whether satisfaction is uniformly distributed or driven by a subset of the sample.

### 4. Aadhaar Usage Rate by Service Type
The current analysis covers banking and telecom. The dataset likely contains service usage columns for PDS (ration cards), MGNREGS (employment guarantee), and LPG subsidies. A systematic comparison of Aadhaar usage rates across all welfare schemes would show where integration is deepest and where exclusion is most costly.

### 5. Vulnerable Group Profile Comparison
Migrant workers (2.3% coverage), the homeless (7.7%), and the elderly (22.2%) each lack Aadhaar for different structural reasons — mobility, address verification, physical access. Comparing their barrier profiles (using "reason for not having Aadhaar" columns) would allow targeted policy recommendations rather than generic outreach.

### 6. Centre Count vs. Enrolment Regression
The current finding (174 rural centres → 828 enrolments, 214 urban → 1,172) is descriptive. An OLS regression across districts using full records would quantify the marginal enrolment gain per additional centre, producing an actionable estimate for infrastructure investment.

### 7. Third Gender Access Barriers
Zero recorded Aadhaar holders in the third gender sample is a striking finding. Whether this reflects actual non-possession or data collection failure (social stigma preventing honest reporting) would require a qualitative follow-up or chi-square test against the survey's own "reason not enrolled" categories.

### 8. School Admission Compliance Mapping
230 respondents faced mandatory Aadhaar requirements for school admission; 47 were denied. Mapping these by state would reveal whether certain states have systematically non-compliant school administrations — useful for targeted regulatory enforcement.

### 9. Longitudinal Comparison
The State of Aadhaar initiative ran surveys in 2017 and 2019. A diff-in-diff analysis comparing enrolment rates, service integration, and sentiment between these two waves would show whether Aadhaar's rollout improved over time and which problems persisted.

### 10. Machine Learning: Predicting Aadhaar Absence
Train a classification model (logistic regression, random forest) on demographic features — state, gender, religion, occupation, settlement size — to predict Aadhaar non-possession. Feature importances would objectively identify the strongest predictors of exclusion, going beyond the univariate breakdowns in the current analysis.

---

Data sourced from the [State of Aadhaar 2019](https://stateofaadhaar.in/) initiative. Analysis covers the 2019 in-depth survey across 28 Indian states.
