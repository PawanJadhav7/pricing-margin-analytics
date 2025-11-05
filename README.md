# 💰 Pricing & Margin Analytics — AWS • Snowflake • dbt • Airflow • Tableau

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Snowflake](https://img.shields.io/badge/Snowflake-Cloud%20Warehouse-blue)
![dbt](https://img.shields.io/badge/dbt-Analytics-orange)
![AWS](https://img.shields.io/badge/AWS-S3%2C%20Glue%2C%20EventBridge-yellow)
![Tableau](https://img.shields.io/badge/BI-Tableau%20%7C%20PowerBI-blueviolet)

End-to-end **financial data engineering and analytics pipeline** that calculates **Pocket Margin**, identifies **margin leakages** (discounts, promos, rebates, freight), and models **price elasticity** by product and customer. Built to demonstrate production-grade **AWS → Snowflake → dbt → Airflow → Tableau** orchestration.

---

### ⚙️ Tech Stack
- **AWS:** S3 (raw/curated zones), Glue (schema & transformations), EventBridge (scheduling)
- **Warehouse:** Snowflake (Bronze → Silver → Gold layers)
- **Transformations:** dbt (models, tests, lineage)
- **Orchestration:** Airflow (MWAA) for DAG-based workflow automation
- **Analytics:** Python (elasticity, what-if simulator)
- **Visualization:** Tableau / Power BI (executive dashboards)

---

### 📊 Key Outputs
- **Margin Waterfall Dashboard** (List → Invoice → Net → Pocket)
- **Leakage Analytics** (Discounts, Rebates, Freight, Promotions)
- **Elasticity Model** (Price vs. Quantity response curve)
- **Customer Profitability Heatmaps**
- **BI Layer Refresh via Airflow DAG**

---

### 🧠 Example Flow
**AWS S3 → Snowflake (SILVER → GOLD) → dbt → Airflow → Tableau**

This architecture follows a **Medallion Lakehouse** pattern optimized for finance analytics workloads — enabling incremental processing, governed transformations, and seamless BI refreshes.

---

### 📁 Repository Structure
```text
pricing-margin-analytics/
│
├── src/
│   ├── generator/          # Synthetic data generator (sales, cost, pricing)
│   │   └── make_dataset.py
│   ├── loaders/            # Scripts to load CSVs → Snowflake (SILVER)
│   │   └── load_silver.py
│   ├── gold/               # dbt-style SQL models for Gold marts
│   │   └── create_gold_views.py
│   └── elasticity/         # Python model for price elasticity and what-if
│       └── fit_elasticity.py
│
├── data/                   # Local sample datasets (CSV)
├── assets/                 # Diagrams, visuals, dashboards
│   └── diagrams/
│       └── pricingandmarginarchidiagram.png
│
├── dags/                   # Airflow DAGs (pricing_pipeline_dag.py)
├── dbt/                    # dbt project files and models
├── quality/                # Great Expectations or DQ tests
├── requirements.txt         # Python dependencies
├── .env.sample              # Snowflake & AWS credentials (template)
├── .gitignore               # Ignored files & folders
└── README.md                # This documentation
```
---

### 🚀 Getting Started
**1️⃣ Create and activate a virtual environment**
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
**2️⃣ Generate synthetic data**
```bash
python src/generator/make_dataset.py
```
**3️⃣Load into Snowflake**
```bash
python src/loaders/load_silver.py
```
**4️⃣ Transform and model**
```bash
dbt run --select gold.*
```

**5️⃣ Visualize in Tableau/Power BI**
```
Connect to PRICING_DB.GOLD and explore Margin Waterfall & Elasticity Dashboards.
```
🔗 Live Case Study
```
👉 [View on Portfolio → Pricing & Margin Analytics](https://pawanjadhav.cloud/pricingandmarginanalytics/)￼
```
