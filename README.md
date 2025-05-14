
# Customer Churn Prediction using Survival Analysis

## Project Overview
This project applies **survival analysis** to model and predict customer churn using time-to-event data. We leverage non-parametric, semi-parametric, and parametric methods to:

- Estimate retention curves  
- Identify key churn drivers  
- Predict individual customer churn timelines  
- Provide actionable insights for customer retention strategy  

Understanding when and why customers leave is crucial—especially when retention is more cost-effective than acquisition.

---

## Dataset
- **Source:** [Maven Analytics Data Playground](https://www.mavenanalytics.io/data-playground?search=churn)  
- **Features:** Demographics, tenure, contract type, internet type, churn status, etc.  
- **Highlights:**
  - Clearly defined churn events
  - Time-to-event values
  - Rich customer metadata
 
## Tech Stack

- **Python 3.9+**
- **Pandas** – Data manipulation  
- **NumPy** – Numerical operations  
- **Matplotlib / Seaborn** – Visualization  
- **Lifelines** – Survival analysis (Kaplan-Meier, AFT, CoxPH models)  
- **Scikit-learn** – Data preprocessing and metrics  
- **Jupyter Notebook** – Interactive development  

---

## Approach

### 1. Non-Parametric Analysis
- Kaplan-Meier estimator used to plot survival curves  
- Log-rank tests applied to compare survival curves across customer groups (e.g., gender, marital status)

### 2. Parametric Survival Model (AFT)
- Evaluated several distributions, selected **Log-Normal** based on lowest AIC  
- Predicts expected time to churn per customer  
- Estimates multiplicative effect of covariates

### 3. Cox Proportional Hazards Model
- Initial model violated proportionality assumptions  
- Used **Stratified Cox model with time-varying covariates**  
- Captured dynamic effects such as fading influence of marketing offers over time

---

## Evaluation Metrics

- **Concordance Index (C-index):**
  - Log-Normal AFT model: ~0.83  
  - Stratified Cox model: ~0.81  
- **Other Diagnostics:**
  - Residual plots, Q-Q plots  
  - `lifelines` package used for assumption checks and diagnostics

---

## Key Observations

- 10% of customers churn within the first 5 months — early engagement is vital  
- **Yearly contracts** reduce churn hazard ~24x compared to monthly plans  
- **Married users** churn 40% less than single users  
- **Credit card payers** churn less than others  
- Offers initially increase hazard but risk drops with tenure — incentive duration matters



