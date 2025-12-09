# Fraud Detection with XGBoost  
*A Machine Learning model for identifying fraudulent financial transactions using XGBoost and SHAP Explainable AI.*


## Project Overview

Financial fraud is a major challenge for banks and fintech companies.  
Fraudulent transactions are **rare**, **costly**, and **hard to catch** without advanced analytics.

In this project, I built a **Fraud Detection Machine Learning model** using:

- **Simulated real-world banking transaction data**
- **XGBoost** (industry standard for tabular ML)
- **Explainable AI (SHAP)** to interpret model decisions
- **Class imbalance handling** for realistic fraud scenarios

This project demonstrates a full end-to-end workflow that would be used inside a financial institution such as Lloyds, Barclays, or Capital One.




## Objectives

- Generate a realistic synthetic fraud dataset  
- Preprocess and encode features  
- Train an XGBoost model tailored for imbalanced data  
- Evaluate performance using ROC-AUC, precision, recall, confusion matrix  
- Explain individual predictions using SHAP values  
- Build a transparent and interpretable model suitable for regulated industries  




## Project Structure

fraud-detection-xgboost/

│

├── fraud_detection_xgboost.ipynb     # Main notebook

├── fraud.csv                          # Dataset (generated in notebook)

└── README.md                          # Documentation (this file)




## Dataset Description

The dataset simulates realistic banking transactions.

| Feature | Description |
|--------|-------------|
| `amount` | Transaction amount |
| `oldbalanceOrg` | Sender's balance before transaction |
| `newbalanceOrig` | Sender's balance after transaction |
| `oldbalanceDest` | Receiver's balance before transaction |
| `newbalanceDest` | Receiver's balance after transaction |
| `transaction_type` | TRANSFER or CASH_OUT |
| `isFraud` | Target variable (0 = legitimate, 1 = fraud) |

Fraud patterns were applied based on real financial behaviour:
- High transaction amounts  
- TRANSFER type more likely fraud  
- Sender balance significantly lower than transaction amount  
- Destination balances unusually high  

Fraud ratio ≈ **20%** for easier model training.


## Preprocessing Steps

- One-hot encoding for categorical transaction type  
- Feature/target separation  
- Train-test split with stratification  
- Handling class imbalance with **scale_pos_weight**  
- Normalization not required due to tree-based algorithm  


## Model: XGBoost Classifier

XGBoost was chosen because:

- Performs exceptionally well on tabular financial datasets  
- Handles class imbalance efficiently  
- Robust against overfitting  
- Works seamlessly with SHAP explainability  

Key parameters used:

```python
model = xgb.XGBClassifier(
    n_estimators=300,
    learning_rate=0.1,
    max_depth=5,
    subsample=0.8,
    colsample_bytree=0.8,
    scale_pos_weight=scale_pos_weight,
    eval_metric="logloss",
    random_state=42
)
````


## Model Evaluation

Metrics calculated:

* **Classification report** (Precision, Recall, F1-score)
* **Confusion matrix**
* **ROC-AUC Score**
* **Probability predictions** for threshold analysis

Particularly important:

* **Recall for fraud (Class 1)** → measures how many frauds the model catches
* **False negatives** must stay low for banking use cases


## Explainable AI (SHAP)

To make the model transparent and regulator-friendly:

* Global interpretation: `shap.summary_plot()`
* Local interpretation: `shap.force_plot()`

SHAP identifies features that increased or decreased the fraud probability for both the entire dataset and each individual transaction.

Example insights:

* Higher transaction amounts increased fraud probability
* TRANSFER-type transactions carried higher risk
* Extremely high destination balances were suspicious
* Normal sender balances reduced likelihood of fraud


## Key Insights

* XGBoost provides strong predictive performance for fraud scenarios
* Handling class imbalance is critical
* Explainability is **mandatory** for risk and compliance teams
* SHAP allows model decisions to be audited and trusted
* This workflow mirrors real-world fraud detection systems


## Future Improvements

* Add SMOTE or ADASYN oversampling
* Hyperparameter tuning with Optuna
* Model comparison: LightGBM, CatBoost
* Deploy model as an API using FastAPI or Flask
* Build a dashboard with Streamlit


## Author

Emine Ceran
Financial Data Science Journey

GitHub: [https://github.com/ebceran](https://github.com/ebceran)]

LinkedIn: (https://www.linkedin.com/in/emine-ceran-03b26159/ )




## Acknowledgements
