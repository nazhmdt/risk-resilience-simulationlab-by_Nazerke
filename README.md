# ⚠️ Marketing Risk & Resilience Simulation Lab

> End-to-end marketing risk analytics project — from advertising performance data to Monte Carlo simulation, anomaly detection, reputation risk scoring, and Power BI dashboard.

---

## 📌 Overview

This project focuses on marketing risk and resilience analysis using advertising performance data.

The goal is to evaluate campaign performance, simulate future campaign risk, detect abnormal marketing behavior, and assess potential brand reputation risks.

The project combines:

- advertising performance analysis
- ROI and efficiency metrics
- Monte Carlo risk simulation
- VaR and CVaR risk metrics
- Isolation Forest anomaly detection
- LLM-based reputation risk scoring
- Power BI dashboard for business interpretation

---

## 📂 Project Structure

```text
marketing-risk-resilience-lab/
├── risk&resilence_simulationlab_withoutkey.ipynb   # Full risk simulation and analytics pipeline
├── risk&resilence_simulationlab_bi.pbix            # Power BI dashboard
└── README.md
```

---

## 🔍 Analysis Pipeline

**1. Data Loading & Inspection**  
- Loaded advertising performance data
- Used real advertising data or generated a synthetic replica if the dataset was not available
- Checked dataset structure and basic statistics
- Worked with advertising channels: TV, Radio, and Newspaper

**2. Feature Engineering**
- Created `Total_Spend`
- Created `ROI`
- Created `CPR` — cost per revenue unit
- Created `TV_Share`
- Created `Radio_Share`
- Created rolling 4-week averages
- Created `Low_ROI_Flag` based on the bottom 10% ROI threshold

**3. Exploratory Risk Analysis**
- Analyzed channel spend vs sales
- Compared TV and Radio spend efficiency
- Reviewed ROI distribution
- Analyzed channel mix over time
- Identified low-efficiency campaign periods

**4. Monte Carlo Campaign Risk Simulation**
- Fitted empirical distributions to campaign data
- Simulated **10,000 future campaign scenarios**
- Estimated possible ROI outcomes under uncertainty
- Measured downside risk using risk metrics

**5. Risk Metrics Calculation**
Calculated key campaign risk indicators:

- `VaR(5%)` — worst-case ROI in the bottom 5% of scenarios
- `VaR(10%)` — worst-case ROI in the bottom 10% of scenarios
- `CVaR` — average ROI in the worst 5% of scenarios
- `Probability of Loss` — probability that ROI will be below 0%
- `Best Case`
- `Worst Case`

**6. Sensitivity Analysis**
- Built a tornado-style sensitivity analysis
- Tested how different factors affect mean ROI
- Compared the impact of market conditions, TV allocation, radio efficiency, total budget, and newspaper efficiency

**7. ML Anomaly Detection**
- Built risk-related features using rolling z-scores and percentage changes
- Trained an `IsolationForest` model
- Detected anomalous campaign weeks
- Identified abnormal patterns in sales, spend, ROI, and cost efficiency

**8. Reputation Risk Scoring**
- Generated synthetic social media posts about the brand
- Used an LLM-based scorer to classify reputation risk
- Scored each post by:
  - sentiment
  - risk level
  - risk category
  - urgency
  - reasoning

**9. Brand Risk Index**
- Built a weighted Brand Risk Index from 0 to 100
- Applied higher weights to urgent and critical posts
- Added penalties for legal, viral, data breach, and reputation risks
- Classified brand status as low, moderate, or high risk

**10. Export for Power BI**
- Exported campaign performance, anomaly results, Monte Carlo results, and reputation risk outputs
- Built Power BI dashboard pages for business interpretation

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikitlearn&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=flat&logo=scipy&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)
![OpenPyXL](https://img.shields.io/badge/OpenPyXL-217346?style=flat)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat&logo=powerbi&logoColor=black)

---

## 💡 Key Findings

- ROI analysis helps identify inefficient campaign periods.
- Monte Carlo simulation allows the business to estimate future campaign risk before making budget decisions.
- VaR and CVaR help measure downside risk instead of only looking at average ROI.
- Isolation Forest can detect abnormal campaign weeks that may not be visible from simple charts.
- Reputation risk scoring helps identify posts that may require urgent brand response.
- Brand Risk Index provides a simple business-friendly score for monitoring reputation risk.
- Power BI dashboard helps translate technical risk metrics into clear business insights.

---

## 📊 Risk Metrics Used

| Metric | Meaning | Business Use |
|---|---|---|
| ROI | Return on investment | Measures campaign profitability |
| CPR | Cost per revenue unit | Shows campaign efficiency |
| VaR(5%) | Worst-case ROI in the bottom 5% of scenarios | Helps estimate downside campaign risk |
| CVaR | Average ROI in the worst 5% of scenarios | Shows expected loss in bad scenarios |
| Probability of Loss | Probability that ROI is below 0% | Helps estimate chance of unprofitable campaigns |
| Brand Risk Index | Weighted reputation risk score from 0 to 100 | Helps monitor brand reputation health |

---

## 🤖 Models and Methods Used

| Method | Purpose | Business Use |
|---|---|---|
| Monte Carlo Simulation | Simulate future campaign ROI scenarios | Campaign risk forecasting |
| VaR / CVaR | Measure downside risk | Budget risk management |
| Tornado Sensitivity Analysis | Compare impact of risk drivers | Identify the most important risk factors |
| Isolation Forest | Detect anomalous campaign weeks | Find unusual spend, sales, or ROI behavior |
| LLM Risk Scorer | Analyze social media reputation risk | Identify posts requiring response |
| Brand Risk Index | Summarize reputation risk | Create a simple brand risk monitoring score |

---

## 🚨 Anomaly Detection

The project uses **Isolation Forest** to detect unusual marketing performance patterns.

Features used for anomaly detection include:

- `Total_Spend_zscore`
- `Sales_zscore`
- `ROI_zscore`
- `CPR_zscore`
- `Spend_pct_change`
- `Sales_pct_change`
- `ROI_pct_change`
- `TV_Radio_Ratio`
- `Efficiency_Drop`

The model flags weeks where campaign performance strongly deviates from normal behavior.

Possible business explanations for anomalies:

- sudden budget misallocation
- competitor activity
- channel saturation
- weak campaign creative
- unexpected market changes
- inefficient media spend

---

## 🧠 Reputation Risk Scoring

The project includes a reputation risk scoring module based on synthetic social media posts.

Each post is classified by:

- sentiment: positive, neutral, or negative
- risk level: from 0 to 10
- risk category: none, product, reputation, legal, viral, or data breach
- urgency: low, medium, high, or critical

This helps the business identify which posts require faster attention from the marketing or PR team.

---

## 📈 Power BI Dashboard

A Power BI dashboard was created to make the risk analysis easier to understand for business users.

The dashboard includes:

**1. Campaign Performance Overview**
- KPI cards
- spend vs sales trend
- ROI performance
- channel spend comparison

**2. Risk Heatmap**
- ROI volatility by channel
- risky time periods
- low-efficiency campaign weeks

**3. Anomaly Timeline**
- detected anomaly weeks
- spend and sales behavior
- anomaly score visualization

**4. Brand Risk Gauge**
- Brand Risk Index score
- traffic-light risk status
- reputation risk overview

**5. Monte Carlo Summary**
- VaR and CVaR summary
- probability of loss
- risk band analysis

---

## 📌 Business Recommendations

### 1. Monitor ROI risk before scaling campaigns

Campaigns should not be evaluated only by average ROI.

Recommended actions:
- track VaR and CVaR
- compare expected ROI with downside risk
- avoid scaling campaigns with high loss probability
- use simulation before major budget increases

---

### 2. Investigate anomaly weeks

Anomalous weeks should be reviewed by the marketing team.

Recommended actions:
- check campaign creatives
- review channel budget allocation
- compare performance with competitor activity
- analyze whether the anomaly was caused by spend spikes or sales drops

---

### 3. Use sensitivity analysis for budget planning

Sensitivity analysis shows which factors have the strongest effect on ROI.

Recommended actions:
- focus on the most influential campaign drivers
- test budget allocation changes
- reduce dependence on unstable channels
- prepare alternative budget scenarios

---

### 4. Track brand reputation risk continuously

Social media risk can quickly affect brand perception.

Recommended actions:
- monitor high-risk posts
- prioritize critical and viral risks
- create fast response rules for PR issues
- combine reputation risk with campaign performance data

---

## 📌 Business Value

This project shows how risk analytics can improve marketing decision-making.

The results can help a business:

- estimate future campaign risk
- detect abnormal marketing performance
- improve budget allocation
- reduce inefficient ad spend
- monitor brand reputation
- prepare for negative scenarios
- build a more resilient marketing strategy
- support data-driven decision-making

---

## 👥 Team

**Nazerke Zhumadilova** · [@nazhmdt](https://github.com/nazhmdt)  
**Inzhu Nurlan** · [@InzhuNurlan](https://github.com/InzhuNurlan)

---

## 🎓 Course

**AI in Marketing** — Astana IT University  
Instructor: **Muhammed Ali Ibrahim**
