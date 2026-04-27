# Retail Loan Portfolio & Risk Exposure Analysis

## 📌 Business Objective
In the highly regulated BFSI sector, accurately predicting credit default and managing portfolio exposure is critical for capital preservation. This end-to-end data pipeline simulates a real-world credit risk environment. It transitions from raw data engineering to predictive machine learning, and finally to business rule implementation, dynamically translating mathematical probabilities into actionable CIBIL-style credit scores.

## 🛠️ Tech Stack & Architecture
* **Data Engineering & ETL:** Python (Pandas, Numpy, Faker), SQLAlchemy, MySQL.
* **Machine Learning:** Scikit-Learn (Logistic Regression with class-weight balancing).
* **Business Intelligence:** Power BI (DAX, Interactive Data Storytelling).

## 🚀 Execution Flow

### Phase 1: Data Generation & Database Engineering
* Generated a highly correlated, statistically realistic dataset of 5,000 retail customers.
* Engineered critical financial features such as **Debt-to-Income (DTI) Ratio** and **Credit Utilization**.
* Deployed an automated ETL pipeline to push raw data directly into a local MySQL Data Warehouse.

### Phase 2: Predictive Modeling (Probability of Default)
* Extracted and pre-processed data via SQL queries.
* Trained a Logistic Regression model optimized for **Recall (90%)** on minority class (Defaulters) using `class_weight='balanced'`.
* Prioritized the detection of High-Risk profiles (False Negatives) to minimize the bank's Expected Credit Loss (ECL).

### Phase 3: Business Decision Engine (Credit Scoring)
* Mapped the raw Probability of Default (PD) to a tangible 300-850 CIBIL-style Credit Score scale.
* Implemented algorithmic underwriting rules to segment the portfolio:
    * **Auto-Approve:** Score >= 750 (Low Risk, Instant Revenue)
    * **Manual Review:** Score 600 - 749 (Operational Workload)
    * **Auto-Reject:** Score < 600 (High Risk, Capital Preservation)
* Pushed the final scored dataset (`portfolio_risk_mart`) back to MySQL for reporting.

### Phase 4: Risk Officer Dashboard
* Connected Power BI directly to the MySQL Risk Mart.
* Developed explicitly programmed DAX measures to calculate macro-level KPIs.
* **Key Metrics Tracked:** * Total Loan Book: ₹6.38bn
  * Approval Rate: 47.66%
  * **Portfolio At Risk (PaR): ₹1.85bn** (Capital successfully protected from default).

## 💡 Business Impact
* **Automated Underwriting:** Reduced operational bottleneck by automating decisions for ~80% of the applicant volume.
* **Risk Mitigation:** Actively isolated high-risk toxic assets, protecting ₹1.85bn in potential principal loss.
* **Granular Visibility:** Provided Underwriters with a dynamic, filterable worklist to manually review 'grey area' files, ensuring legitimate revenue opportunities (False Positives) were not blindly discarded.
