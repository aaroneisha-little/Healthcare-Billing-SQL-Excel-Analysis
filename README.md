# Healthcare Billing & Patient Admissions Analysis (SQL & Excel)

## Project Overview
Cleaned, audited, and analyzed a dataset of **55,000+ hospital patient records** using **SQL (SQLite)** and **Excel / Google Sheets** to uncover total billing trends across medical conditions, admission categories, and insurance payers.

### Key Business Questions Answered
* Which medical conditions generate the highest total hospital billing?
* How are patient admissions distributed across Elective, Emergency, and Urgent care?
* How do average claim amounts and patient volumes compare across major insurance providers?

---

## Key SQL Queries

### 1. Total Hospital Billing by Medical Condition
```sql
SELECT medical_conditio AS medical_condition, ROUND(SUM(billing_amount), 2) AS total_billing
FROM healthcare_dataset
GROUP BY medical_conditio
ORDER BY total_billing DESC;
```

### 2. Top 10 Highest-Cost Emergency Room Claims
```sql
SELECT name, medical_conditio AS medical_condition, hospital, ROUND(billing_amount, 2) AS bill
FROM healthcare_dataset
WHERE admission_type = 'Emergency' AND billing_amount > 40000
ORDER BY billing_amount DESC
LIMIT 10;
```

### 3. Average Billing & Patient Volume by Insurance Provider
```sql
SELECT insurance_provid AS insurance_provider, COUNT(*) AS total_patients, ROUND(AVG(billing_amount), 2) AS avg_bill
FROM healthcare_dataset
GROUP BY insurance_provid
ORDER BY avg_bill DESC;
```

---

## Tools & Skills Demonstrated
* **SQL (SQLite):** `SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`, `COUNT`, `SUM`, `AVG`, `ROUND`
* **Excel & Google Sheets:** Data Deduplication, Whitespace Cleaning, Pivot Tables, `COUNTA`, Executive Dashboard Visualization
