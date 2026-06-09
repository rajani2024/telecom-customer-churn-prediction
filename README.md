# Telecom Customer Churn Prediction and Retention Analytics

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Classification-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## Project Overview

Customer churn is one of the most significant challenges faced by telecom service providers. Acquiring a new customer is considerably more expensive than retaining an existing one, making churn prediction a critical business capability.

This project develops machine learning models to identify high-value customers who are likely to churn in the near future and recommends retention strategies based on customer behavior, recharge patterns, and service usage indicators.

In addition to churn prediction, the project also identifies the key drivers of churn, enabling business teams to take proactive actions before customers switch to competing providers.

---

## Business Problem

The telecom industry operates in a highly competitive environment where customers can easily migrate to alternative service providers.

The objectives of this project are:

- Predict whether a high-value customer is likely to churn.
- Identify the factors contributing to churn behavior.
- Support proactive customer retention initiatives.
- Reduce revenue leakage caused by customer attrition.
- Improve customer lifetime value through targeted interventions.

---

## Dataset Description

The dataset contains telecom customer usage and recharge information across multiple months.

The data includes:

- Voice call usage patterns
- Incoming and outgoing call behavior
- Recharge activity
- Data usage metrics
- Average Revenue Per User (ARPU)
- Customer engagement indicators

### Target Variable

| Variable | Description |
|----------|-------------|
| Churn | Indicates whether a customer churned during the churn phase |

---

## Project Objectives

1. Predict customer churn with high recall.
2. Handle severe class imbalance.
3. Reduce dimensionality of a high-dimensional dataset.
4. Evaluate multiple classification algorithms.
5. Compare models using business-oriented metrics.
6. Identify the strongest predictors of churn.
7. Recommend retention strategies based on customer behavior.

---

## Methodology

### Data Preparation

- Missing value treatment
- Feature engineering
- High-value customer identification
- Churn definition based on telecom business rules
- Data standardization

### Handling Class Imbalance

The churn dataset exhibited significant class imbalance.

To address this issue:

- SMOTE (Synthetic Minority Oversampling Technique) was applied to the training dataset.
- This helped improve the model's ability to identify churn customers.

### Dimensionality Reduction

The original dataset contained a large number of features.

Principal Component Analysis (PCA) was used to:

- Reduce dimensionality
- Remove redundancy
- Improve computational efficiency
- Minimize noise

### PCA Configuration

| Parameter | Value |
|------------|---------|
| Number of Principal Components | 75 |

---

## Models Evaluated

The following classification algorithms were evaluated:

1. Logistic Regression (GLM)
2. Decision Tree
3. Random Forest
4. AdaBoost
5. XGBoost

---

## Model Performance Comparison

### Test Dataset Performance

| Model | Accuracy | Precision | Recall | AUC |
|---------|---------|---------|---------|---------|
| Logistic Regression | 0.84 | 0.37 | 0.82 | 0.83 |
| Decision Tree | 0.84 | 0.33 | 0.62 | 0.74 |
| Random Forest | 0.90 | 0.50 | 0.68 | 0.80 |
| AdaBoost | 0.83 | 0.35 | 0.81 | 0.82 |
| XGBoost | 0.91 | 0.53 | 0.63 | 0.78 |

---

## Model Selection Strategy

The best model depends on the business objective.

### Use Case 1: Identify Maximum Churn Customers

Business Goal:

> Capture the highest possible number of customers likely to churn.

Evaluation Metrics:

- Recall
- AUC

### Selected Model: AdaBoost

Configuration:

- PCA Components: 75
- SMOTE Applied
- n_estimators = 200

Performance:

| Metric | Value |
|---------|---------|
| Accuracy | 0.83 |
| Precision | 0.35 |
| Recall | 0.81 |
| AUC | 0.82 |

### Why AdaBoost?

AdaBoost correctly identifies approximately **81% of churn customers**, making it highly suitable for customer retention campaigns.

Although Precision is relatively low, the business impact of missing a churn customer is significantly higher than offering retention incentives to some non-churn customers.

---

### Use Case 2: Balanced Classification Performance

Business Goal:

> Correctly classify both churn and non-churn customers.

Evaluation Metric:

- Accuracy

### Selected Model: Random Forest

Configuration:

- PCA Components: 75
- SMOTE Applied
- n_estimators = 200
- max_depth = 40
- min_samples_leaf = 10

Performance:

| Metric | Value |
|---------|---------|
| Accuracy | 0.90 |
| Precision | 0.50 |
| Recall | 0.68 |
| AUC | 0.80 |

### Why Random Forest?

Random Forest provides the best balance between:

- Accuracy
- Precision
- Recall

making it suitable for general-purpose churn classification.

---

## Identifying Churn Drivers

While PCA-based models provide strong predictive performance, PCA components are difficult to interpret.

To identify business-relevant churn indicators, a Logistic Regression model was used.

---

## Top Predictors of Customer Churn

| Feature | Business Meaning |
|----------|----------|
| loc_ic_t2m_mou_8 | Incoming calls from other mobile operators |
| spl_ic_mou_8 | Special incoming call minutes |
| loc_ic_t2f_mou_8 | Incoming calls from fixed-line users |
| av_rech_amt_data_8 | Average data recharge amount |
| total_rech_num_8 | Total number of recharges |
| loc_og_t2t_mou_8 | Outgoing calls within the same operator |
| last_day_rch_amt_8 | Last recharge amount |
| arpu_3g_8 | 3G revenue contribution |
| loc_ic_t2t_mou_8 | Incoming calls within same operator |
| arpu_7 | Revenue generated in July |

---

## Key Business Insights

### Declining Usage Signals Churn Risk

Customers exhibiting reductions in:

- Incoming calls
- Outgoing calls
- Recharge frequency
- Recharge amounts

show a significantly higher probability of churn.

### Customer Engagement is Critical

Reduced engagement with telecom services consistently emerged as one of the strongest indicators of churn.

### Revenue Indicators Matter

ARPU-related variables demonstrated a strong relationship with churn behavior.

Customers showing declining revenue contribution should be prioritized for retention programs.

---

## Recommendations and Retention Strategy

### Early Warning System

Deploy the AdaBoost model to identify customers with a high probability of churn.

### Monitor Key Churn Indicators

Track customers showing:

- Reduced recharge activity
- Reduced call usage
- Declining ARPU
- Lower engagement levels

### Personalized Retention Campaigns

Offer:

- Customized recharge plans
- Bonus data packages
- Loyalty rewards
- Targeted promotional offers

to customers identified as high risk.

### Revenue Protection

Customers exhibiting declining engagement patterns should be targeted before entering the churn phase to minimize revenue loss.

---

## Machine Learning Concepts Demonstrated

This project demonstrates practical application of:

- Classification
- Logistic Regression
- Decision Trees
- Random Forest
- AdaBoost
- XGBoost
- PCA
- Dimensionality Reduction
- SMOTE
- Class Imbalance Handling
- Hyperparameter Tuning
- Model Evaluation
- Precision-Recall Tradeoffs
- ROC-AUC Analysis

---

## Limitations

- PCA improves prediction but reduces interpretability.
- Customer support interactions were not included.
- Competitor pricing information was unavailable.
- Customer complaint history was not considered.
- The model does not currently support real-time scoring.

---

## Future Enhancements

Potential future improvements include:

- Real-time churn prediction pipelines
- SHAP-based model explainability
- Customer segmentation using clustering
- Deep learning-based churn prediction
- Integration with CRM systems
- Automated retention recommendation engines

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- XGBoost
- Imbalanced-Learn (SMOTE)
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Repository Structure

```text
telecom-customer-churn-prediction/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── telecom_churn.csv
│
├── notebooks/
│   └── telecom_customer_churn_prediction.ipynb
│
└── reports/
    └── figures/
```

---

## How to Run

### Clone Repository

```bash
git clone https://github.com/<your-github-username>/telecom-customer-churn-prediction.git
```

### Navigate to Project Directory

```bash
cd telecom-customer-churn-prediction
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Launch Notebook

```bash
jupyter notebook notebooks/telecom_customer_churn_prediction.ipynb
```

---

## Author

This project was completed as part of the Machine Learning and AI learning journey, focusing on solving real-world customer retention challenges through predictive analytics and business-driven machine learning.