# 🏦 Bank Customer Retention — Predictive Analytics Project
### Financial Service Excellence & Customer Experience (CX) Analytics

---

## 📌 Project Overview

Modern banks struggle to bridge the gap between **customer feedback** and **employee development**. Without a clear data link between these two points, HR and management cannot effectively pinpoint regional service friction, correlate customer sentiment with retention risk, or identify high-value interactions to model in staff training.

This project builds an **end-to-end data pipeline** that transforms raw customer interaction data into actionable insights — helping HR departments and leadership make data-informed decisions on staff training, regional resource allocation, and proactive retention campaigns.

**Dataset:** 1,000 retail banking customers with 11 features covering demographics, product engagement, satisfaction scores, and retention status.

**Target Stakeholder:** Human Resources & Talent Management / Senior Leadership

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Python (Pandas, NumPy) | Data cleaning, transformation, feature engineering |
| SQLAlchemy + SQLite | ETL pipeline, database storage, analytical queries |
| SQL | Business intelligence queries & customer segmentation |
| Matplotlib & Seaborn | Exploratory data analysis & inline visualisation |
| Scikit-learn | Logistic Regression churn prediction model |
| Power BI | Executive dashboard for stakeholder reporting |

---

## 📂 Project Structure

```
bank-customer-retention/
│
├── Bank_Customer_Retention_Predictive_Analytics.ipynb   # Full pipeline notebook
├── bank_retention_final_PBI.csv                         # Cleaned export for Power BI
├── churn_drivers_chart.png                              # Feature importance visualisation
└── README.md
```

---

## 🔄 Project Workflow

### Phase 1 — Data Ingestion & Environment Setup
Loaded raw customer data (`customer_experience_data.csv`) into Python and conducted a preliminary structural review before migration to a relational database.

### Phase 2 — Data Cleaning & Audit
Performed a thorough data quality audit across 1,000 records:
- Verified zero missing values and zero duplicate rows
- Standardised categorical strings (Location, Gender) for uniform visualisation
- Removed ML-specific encoded columns from the reporting schema
- Validated all numerical ranges (Age, Satisfaction Scores) against business logic

### Phase 3 — ETL Pipeline (SQLite via SQLAlchemy)
Migrated the cleaned DataFrame into a portable SQLite database (`bank_analytics.db`) using SQLAlchemy's `create_engine`. This enables:
- Zero-configuration database setup within the notebook environment
- Direct Power BI connectivity via a single `.db` file
- Reproducible, serverless analytical queries

### Phase 4 — SQL Exploratory Analysis (5 Business Questions)

**1. Sentiment Split**
Customer base is equally divided between Positive and Negative advocates (394 each) — a highly polarised environment. Critically, Negative customers purchase *more* on average (10.46 items vs 10.29) — meaning our most valuable users are our most dissatisfied. This is a **Revenue at Risk** signal.

**2. Geographic Market Analysis**
- Urban, Suburban, and Rural segments are nearly equal in size
- Urban sector shows the lowest average satisfaction (2.92) despite equal population — flagged as primary area for service improvement

**3. Geographic Risk Assessment**
- Urban: 42%+ dissatisfaction rate — highest volume of churn risk
- Suburban: Lowest dissatisfaction rate but the most severe scores among unhappy customers — a "quiet crisis" requiring deep-dive audit

**4. High-Value Churn Watchlist**
Identified the top 10 customers at imminent churn risk: all hold 19 products, 5 of 10 are from Suburban — confirming that Suburban complaints come disproportionately from the bank's most valuable clients.

**5. Digital Sales Friction ("Frustrated Browsers")**
Customers with 45+ product views but fewer than 5 purchases — conversion rates as low as 2%. Customer #588 had a perfect satisfaction score of 5 yet purchased only 1 of 49 viewed items, confirming the barrier is **operational, not emotional**.

### Phase 5 — Demographic Segmentation

| Segment | Key Finding |
|---|---|
| Age 30–50 | Largest, most stable group. Highest satisfaction (3.07) |
| Age 51+ | Buys the most (10.59 products avg) but lowest satisfaction (2.90) — service friction likely driven by digital-first transitions |
| Under 30 | Smallest segment, neutral scores — significant growth opportunity |
| Gender | Near-identical satisfaction scores. Female customers hold more products on average (10.59) — higher ecosystem integration |

### Phase 6 — Predictive Modelling (Churn Forecasting)

**Algorithm:** Logistic Regression (binary classification: Churn = 1, Retained = 0)
**Split:** 80% training / 20% testing
**Accuracy:** 69%

| Feature | Weight | Direction | Insight |
|---|---|---|---|
| Location | -0.199 | Loyalty anchor | Urban customers are most stable despite lower satisfaction — high switching costs |
| Gender | +0.116 | Churn driver | Male customers are "less tethered" — fewer products, higher exit propensity |
| Products Viewed | -0.006 | Weak anchor | Browsing signals engagement, not frustration |
| Age | +0.005 | Neutral | Behaviour matters more than life stage |
| Products Purchased | -0.002 | Weak anchor | More products = slightly more loyal, but not decisively |

---

## 💡 Key Insights & Strategic Recommendations

### 1. Proactive Retention for the "Flight Risk" Segment
**Target:** Male customers with low product counts
**Action:** Launch a "Multi-Product Loyalty" campaign. Bundled services (insurance, high-yield savings) increase switching costs and reduce churn propensity.

### 2. Service Recovery for "Captive" Urban Centres
**Target:** Urban Senior customers (satisfaction 2.51–2.80)
**Action:** These customers stay despite being unhappy — they are prime targets the moment a competitor enters the market. Improving senior branch service is a **defensive necessity**, not optional.

### 3. Digital UX Optimisation
**Target:** High-volume browsers (40+ views, <5 purchases)
**Action:** Deploy personalised offers or Live Chat assistance at the "Add to Product" stage. Converting existing engagement into ownership is the highest-ROI intervention available.

---

## 📊 Power BI Dashboard

The cleaned dataset was exported as `bank_retention_final_PBI.csv` for Power BI visualisation. The dashboard covers:
- Churn Rate % by Location, Gender, and Age Group
- Satisfaction Gap by Region
- High-Value Customer Watchlist
- Feature Importance — Churn Drivers vs Loyalty Anchors

*(Screenshots coming soon)*

---

## 📈 Model Performance Summary

| Metric | Value |
|---|---|
| Algorithm | Logistic Regression |
| Training Set | 800 records (80%) |
| Test Set | 200 records (20%) |
| Overall Accuracy | 69% |
| Primary Churn Signal | Location (Urban Effect) |

---

## 👤 About the Author

**Cantwel Njeri Otieno** — Data Analyst | Nairobi, Kenya

- 🔗 [LinkedIn](https://www.linkedin.com/in/njery-cantwel/)
- 🐙 [GitHub](https://github.com/cantwelotieno-commits)
- 📧 cantwel.otieno@gmail.com
