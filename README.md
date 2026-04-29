# 🏥 Healthcare SQL Analysis
### Exploratory Clinical Data Analysis with Advanced SQL ##

---

## 📋 Project Overview ##

This project applies advanced SQL to a simulated clinical dataset inspired by **MIMIC-IV** — the gold standard for clinical data in healthcare AI research.

The goal is not just to write queries, but to answer **real business and clinical questions** of the type that precede an AI project in healthcare: patient readmission, risk stratification, pharmacological patterns, and longitudinal biomarker tracking.

> Built as part of a career transition toward **AI Product Management and AI Strategy in Healthcare**.

---

## 🗂️ Dataset Structure ##

A relational schema with 5 tables simulating a hospital information system:

| Table | Description |
|---|---|
| `patients` | Demographics: gender, age, insurance type |
| `admissions` | Hospital admissions with dates and diagnosis |
| `diagnoses` | ICD-coded diagnoses per admission |
| `prescriptions` | Drug prescriptions per admission |
| `lab_results` | Lab test results (glucose, creatinine) |

---

## 🔧 Technical Skills Demonstrated ##

| Concept | Applied in |
|---|---|
| INNER / LEFT / Self JOIN | Cases 1, 2, 3 |
| GROUP BY + HAVING | Cases 2, 3, 4 |
| Scalar subqueries | Case 5 |
| CTEs (Common Table Expressions) | Cases 4, Q1, Q3, Q5 |
| Window Functions: ROW_NUMBER, LAG, AVG OVER | Cases 6, 7, 8, Q1 |
| Multi-CTE queries | Question 5 |

---

## 🏢 Business Questions Answered ##

### Q1 — 30-Day Readmission by Diagnosis ##
> Which diagnoses have the highest readmission rate within 30 days of discharge?

**Technique:** CTE + LAG() window function  
**Clinical relevance:** 30-day readmissions are the most internationally regulated quality-of-care KPI. AI readmission prediction models are trained on exactly this type of data.

---

### Q2 — Length of Stay by Admission Type and Gender ##
> Are there differences in average length of stay by admission type and patient gender?

**Technique:** Multi-column GROUP BY + JOIN  
**Finding:** Emergency admissions show ~4x longer stays than elective ones, regardless of gender — admission type is the dominant factor.

---

### Q3 — Drug Frequency in High-Risk Patients ##
> Which drugs appear most frequently in patients with multiple admissions?

**Technique:** CTE + triple JOIN  
**Finding:** Furosemide leads (5 prescriptions), consistent with the high prevalence of heart failure in this patient group.

**Variants included:**
- Most frequent drug in emergency admissions
- Drug prescription differences by patient gender

---

### Q4 — Longitudinal Glucose Tracking ##
> How does blood glucose evolve across admissions for the same patient?

**Technique:** JOIN + WHERE filter + chronological ORDER BY  
**Clinical relevance:** Longitudinal biomarker tracking is the foundation of AI models for early detection of metabolic deterioration.

---

### Q5 — High-Risk Patient Identification ##
> Which patients meet a high-risk profile: more than 1 emergency admission AND average glucose > 150 mg/dL?

**Technique:** Dual CTE + JOIN  
**Finding:** Patient #5 (male, 71 years, Medicare) is the only patient meeting both criteria simultaneously.  
**Clinical relevance:** Multi-criteria risk stratification is the most direct healthcare AI use case — enabling preventive interventions before the next emergency visit.

---

## 🔬 Technical Consolidation Cases ##

Eight progressive exercises covering the full SQL skill set:

1. **Self-join** — days between admissions per patient
2. **GROUP BY + HAVING** — diagnoses appearing in more than 2 admissions
3. **Aggregation** — average length of stay by admission type
4. **CTE** — patients with multiple emergency admissions
5. **Scalar subquery** — admissions above average length of stay
6. **ROW_NUMBER() vs RANK()** — chronological admission numbering
7. **LAG()** — previous admission date per patient
8. **AVG() OVER()** — cumulative average length of stay

---

## 💡 Key Insights ##

- **Heart failure** is the most prevalent diagnosis among readmitted patients and the primary driver of Furosemide prescriptions
- **Admission type** (emergency vs elective) is a stronger predictor of length of stay than patient gender
- **Longitudinal SQL analysis** (LAG, window functions) directly translates to feature engineering for predictive AI models
- Multi-criteria risk stratification via SQL is a scalable pre-screening method before deploying ML models

---

## 🚀 Context & Next Steps ##

This project is part of a broader learning path toward **AI Product Management and AI Strategy in Healthcare**, combining:

- Scientific background (Chemistry degree)
- Healthcare business expertise (MBA in Medical Technologies)  
- AI & Innovation training (Master's, Founderz + Microsoft)
- Hands-on technical development (SQL, Python, process automation)

**Next:** Replicating this analysis on real clinical data using **MIMIC-IV** via Google BigQuery.

---

## 🛠️ How to Run ##

1. Open [DB Fiddle](https://www.db-fiddle.com/) and select **PostgreSQL 15**
2. Paste the full contents of `healthcare_sql_analysis.sql` into the **Schema SQL** panel
3. Click **Run**
4. Copy any query from **Section 2 or 3** into the **Query SQL** panel and run

---

*Built with PostgreSQL · Inspired by MIMIC-IV · Oriented toward Healthcare AI*
