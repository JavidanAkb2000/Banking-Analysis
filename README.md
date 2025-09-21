# Banking-Analysis
In this notebook i have deleoped Banking Analysis with STATISTICAL METHODS includign A/B testing and many more. This project was a part of my bootcamp called Gen AI &amp; Data Science.

# Atliqo Banking Analysis 📊

[![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)](https://www.python.org) [![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)](https://jupyter.org) [![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green?logo=pandas&logoColor=white)](https://pandas.pydata.org) [![MySQL](https://img.shields.io/badge/MySQL-Database-blue?logo=mysql&logoColor=white)](https://www.mysql.com)

This Jupyter Notebook (`atliqo_banking.ipynb`) performs exploratory data analysis (EDA) on customer, transaction, and credit profile data from a banking database. The goal is to identify patterns in customer demographics, credit behavior, and spending habits to recommend a target market for a trial credit card launch. It connects to a MySQL database, cleans data, merges datasets, computes metrics by age groups, and visualizes insights.

## Description ℹ️

The notebook analyzes data from the `e_master_card` database to uncover insights into customer profiles, credit scores, and transaction patterns. Key focus areas include:
- Data loading and cleaning 🧹
- Statistical summaries and missing value handling ❌
- Merging datasets for comprehensive analysis 🔗
- Grouping customers by age for targeted metrics (e.g., income, credit limits) 👥
- Visualizations of key metrics 📉
- Recommendations for credit card targeting based on young adults (18-25) 🎯

This project simulates a real-world data wrangling and analysis workflow, emphasizing practical tools for banking/credit insights.

## Libraries Used 🛠️

- **Pandas** 🐼: Data manipulation and analysis
- **NumPy** 🔢: Numerical computations
- **Matplotlib** & **Seaborn** 📊: Data visualization
- **MySQL Connector** 🗄️: Database connection
- **Warnings** ⚠️: Suppress unnecessary warnings

Install dependencies with:
```
pip install pandas numpy matplotlib seaborn mysql-connector-python
```

## Data Sources 📁

- **Database**: MySQL database `e_master_card` (localhost connection with root credentials) 🗃️
  - Tables: `customers`, `transactions`, `credit_profiles`
- **CSV File**: `data/customers.csv` (used for additional customer data) 📄
- Sample Data Previews:
  - Customers: Includes `cust_id`, `name`, `gender`, `age`, `location`, `occupation`, `annual_income`, `marital_status`
  - Transactions: Includes `tran_id`, `cust_id`, `tran_date`, `tran_amount`, `platform`, `product_category`, `payment_type`
  - Credit Profiles: Includes `cust_id`, `credit_score`, `credit_utilisation`, `outstanding_debt`, `credit_inquiries_last_6_months`, `credit_limit`

Note: The notebook assumes a local MySQL setup. Data is loaded via SQL queries and Pandas `read_sql`.

## Analysis Steps 🔍

1. **Setup & Imports** 🚀: Import libraries and suppress warnings.
2. **Database Connection** 🔌: Connect to MySQL and load tables into DataFrames.
3. **Exploratory Data Analysis (EDA)** 🕵️‍♂️:
   - Use `describe()` for statistical summaries (e.g., min/max age, income outliers).
   - Check for missing values with `isnull().sum()`.
   - Load and preview CSV data.
4. **Data Cleaning** 🧼:
   - Fill missing `annual_income` with median.
   - Correct negative `outstanding_debt` to absolute values.
   - Replace invalid ages (e.g., <18 or >100) with median age.
5. **Data Merging** 🔄: Join customers with credit profiles and transactions on `cust_id`.
6. **Feature Engineering** ⚙️:
   - Create age groups (e.g., 18-25, 26-35) using `pd.cut`.
   - Compute metrics like average income, credit limit, and credit score per group.
7. **Visualizations** 📈: Bar plots for age-group metrics using Matplotlib/Seaborn.
8. **Insights & Recommendations** 💡: Analyze young adults for credit card targeting.

## Key Insights 💡

- **Customer Demographics** 👥: Ages range from 1-135 (cleaned for validity); average income ~132k, with outliers.
- **Age Group Metrics** 📊:
  - 18-25 group: ~26% of customers, avg. income <50k, low credit scores/limits due to limited history.
  - Higher age groups show better credit profiles and higher income/limits.
- **Spending Habits** 💳: Low credit card usage in young adults; top categories: Electronics 🔌, Fashion & Apparel 👗, Beauty & Personal Care 💄.
- **No Missing Values Post-Cleaning** ✅: Ensured data integrity.
- **Target Market Recommendation** 🎯: Focus on 18-25 age group for trial credit card launch due to growth potential, despite lower current metrics.

## Visualizations 📈

The notebook includes a 1x3 subplot figure:
- Avg. Annual Income by Age Group (Palette: tab10) 📊
- Avg. Credit Limit by Age Group (Palette: hls) 💰
- Avg. Credit Score by Age Group (Palette: viridis) ⭐

Example output:
Everything is included in notebook please check it up.

## Conclusion 🎯

This analysis highlights opportunities in the young adult segment for credit card products, backed by cleaned data and visualizations. It serves as a foundation for further predictive modeling (e.g., credit risk assessment) or A/B testing launches.

## How to Run 🚀

1. **Setup MySQL** 🗄️: Ensure MySQL is running locally with database `e_master_card` and tables populated.
2. **Clone & Install** 📥:
   ```
   git clone <repo-url>
   cd <repo-folder>
   pip install -r requirements.txt  # If provided, or use libraries above
   ```
3. **Run Notebook** 📓: Open `atliqo_banking.ipynb` in Jupyter:
   ```
   jupyter notebook
   ```
4. **Execute Cells** ▶️: Run top-to-bottom; ensure database credentials match (host: localhost, user/password: root).

For issues, check MySQL connection or data file paths. Contributions welcome! 👏

---

# AtliQo Bank Credit Card A/B Testing Campaign 📊

[![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)](https://www.python.org) [![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)](https://jupyter.org) [![Statsmodels](https://img.shields.io/badge/Statsmodels-Statistics-green?logo=python&logoColor=white)](https://www.statsmodels.org) [![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-blue?logo=pandas&logoColor=white)](https://pandas.pydata.org) [![SciPy](https://img.shields.io/badge/SciPy-Scientific%20Computing-purple?logo=scipy&logoColor=white)](https://scipy.org)

This Jupyter Notebook (`testing_campaign.ipynb`) is Phase 2 of the AtliQo Bank Credit Card Project. It focuses on A/B testing to evaluate a targeted credit card campaign for the untapped market segment of young adults (ages 18-25). The analysis includes pre-campaign sample size calculations, group formation, post-campaign data analysis, visualizations, and hypothesis testing using Z-tests to determine if the campaign increased average transaction amounts.

## Description ℹ️

The notebook builds on insights from the initial analysis, targeting low-credit-history young adults with low credit card usage. It simulates an A/B test:
- **Pre-Campaign**: Calculate required sample sizes based on statistical power, effect size, and significance level.
- **Campaign Execution**: Launch for a test group and form a control group.
- **Post-Campaign**: Analyze transaction data, visualize trends, and perform hypothesis testing to check if the test group shows significantly higher average transactions.
- Key Goal: Validate if the campaign boosts credit card usage in the 18-25 age group for broader rollout.

This phase emphasizes statistical rigor for business decisions, considering budget constraints and effect detection.

## Libraries Used 🛠️

- **Statsmodels** 📈: For power analysis and Z-tests
- **Pandas** 🐼: Data manipulation and loading
- **NumPy** 🔢: Numerical computations
- **SciPy** 🧮: Statistical functions (e.g., normal distribution)
- **Matplotlib** & **Seaborn** 📊: Data visualization

Install dependencies with:
```
pip install statsmodels pandas numpy scipy matplotlib seaborn
```

## Data Sources 📁

- **CSV File**: `avg_transactions_after_campaign.csv` 📄 – Contains daily average transaction amounts for control and test groups post-campaign (columns: `campaign_date`, `control_group_avg_tran`, `test_group_avg_tran`).
- Sample Data Preview:
  | campaign_date | control_group_avg_tran | test_group_avg_tran |
  |---------------|------------------------|---------------------|
  | 2023-09-10   | 259.83                | 277.32             |
  | 2023-09-11   | 191.27                | 248.68             |
  | ...          | ...                   | ...                |

- **Images**: `analysis.png` (insights visualization), `image.png` (Z-test explanation) 🖼️

Data is loaded via Pandas `read_csv`.

## Analysis Steps 🔍

1. **Imports & Setup** 🚀: Load libraries for stats and visualization.
2. **Pre-Campaign Planning** 📐:
   - Define power (0.8), effect size (various, e.g., 0.2-1), alpha (0.05).
   - Use `statsmodels.stats.api.tt_ind_solve_power` to calculate sample sizes for different effect sizes.
   - Select 100 customers for the test group based on business constraints (effect size 0.4).
3. **Group Formation** 👥:
   - Test Group: 100 customers (18-25 age); 40% conversion rate (40 active users).
   - Control Group: 40 exclusive customers for comparison.
4. **Post-Campaign Analysis** 🕵️‍♂️:
   - Load campaign results CSV.
   - Visualize average transactions over time with line plots.
   - Compute means, std devs, and days where control > test (29% of days).
5. **Hypothesis Testing** ⚖️:
   - Null: No difference in means (test ≤ control).
   - Alternative: Test group mean > control mean.
   - Perform manual Z-score calculation and use `statsmodels.stats.weightstats.ztest` (alternative='larger').
   - Results: Z-score ≈2.75, p-value ≈0.003 (reject null at alpha=0.05).

## Key Insights 💡

- **Target Segment (18-25)** 👥: ~25% of customers, avg. income <50k, low credit history/scores/limits, low credit card usage/transactions. Top categories: Electronics 🔌, Fashion & Apparel 👗, Beauty & Personal Care 💄.
- **Sample Size Recommendations** 📏: For effect size 0.4, need ~99 customers per group; aligned with budget for 100-customer trial.
- **Campaign Results** 📈: Test group mean transactions (235.98) > control (221.18); significant difference (p<0.05).
- **Control Outperformance**: On ~29% of days, control had higher averages, but overall test group prevailed.
- **Statistical Outcome**: Reject null hypothesis – campaign positively impacts transaction amounts.

## Visualizations 📈

- **Line Plot**: Daily average transactions for control vs. test groups over 62 days (using Matplotlib/Seaborn).  
  Example output:  
  All included in notebook

## Conclusion 🎯

The A/B test confirms the campaign's effectiveness in increasing average transaction amounts for the 18-25 segment (p=0.003). This supports a full rollout, with potential for further optimization. The notebook demonstrates end-to-end A/B testing, from power analysis to hypothesis validation, aiding data-driven banking decisions.

## How to Run 🚀

1. **Prepare Data** 📂: Ensure `avg_transactions_after_campaign.csv`, `analysis.png`, and `image.png` are in the working directory.
2. **Clone & Install** 📥:
   ```
   git clone <repo-url>
   cd <repo-folder>
   pip install -r requirements.txt  # If provided, or use libraries above
   ```
3. **Run Notebook** 📓: Open `testing_campaign.ipynb` in Jupyter:
   ```
   jupyter notebook
   ```
4. **Execute Cells** ▶️: Run top-to-bottom; adjust parameters like effect sizes or alpha as needed.

For issues, verify CSV paths or library versions. Contributions welcome! 👏

---


*Last Updated: September 21, 2025* 🗓️  
*Author: Javidan Akbarov 
