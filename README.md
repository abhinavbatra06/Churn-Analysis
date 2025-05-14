
# Customer Churn Prediction using Survival Analysis

## Project Overview
This project applies **survival analysis** to model and predict customer churn using time-to-event data. We leverage non-parametric, semi-parametric, and parametric methods to:

- Estimate retention curves  
- Identify key churn drivers  
- Predict individual customer churn timelines  
- Provide actionable insights for customer retention strategy  

Understanding when and why customers leave is crucial especially when retention is more cost-effective than acquisition.

---

## Dataset
- **Source:** [Maven Analytics Data Playground](https://www.mavenanalytics.io/data-playground?search=churn)  
- **Features:** Demographics, tenure, contract type, internet type, churn status, etc.  
- **Highlights:**
  - Clearly defined churn events
  - Time-to-event values
  - Rich customer metadata
 
## Tech Stack

- Python  
- Jupyter Notebook  
- Pandas, NumPy – for data handling  
- Matplotlib, Seaborn – for plots  
- **Lifelines** – for survival analysis models  
- Scikit-learn – for preprocessing    

## Installation

Clone the repository and install the required packages:

```bash
git clone https://github.com/abhinavbatra06/Churn-Analysis.git
cd Churn-Analysis
pip install -r requirements.txt
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
- Switched to **Stratified Cox model with time-varying covariates** to handle changing effects over time  
- Captured dynamic patterns like the fading impact of marketing offers  
- Outputs **hazard ratios**, which describe the **instantaneous rate of churn** relative to a baseline group 

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

- Customers on **yearly billing cycles** churn significantly less than those on monthly plans. Incentivizing longer-term plans can improve retention.
- **Early churn is high**: 10% of users churn within the first 5 months. Improving onboarding and early engagement is critical.
- **Married users churn less**, indicating potential in targeting household plans or bundled services.
- **Offer-driven churn is time-sensitive**: Offers increase churn risk initially, but risk decreases over time. Offer timing and targeting should be optimized.
- **Credit card payment users show lower churn**, suggesting that optimizing for convenience in billing can aid retention.
- **Static churn models underperform**: Time-varying survival models capture churn patterns more accurately, supporting more precise intervention timing.




