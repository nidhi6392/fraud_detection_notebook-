# fraud_detection_notebook-
💳 Fraud Detection using Machine Learning
📌 Overview

This project builds a Fraud Detection System using machine learning to identify fraudulent financial transactions.

The dataset is highly imbalanced, making this a real-world classification problem where detecting fraud (minority class) is more important than overall accuracy.

The project focuses not just on modeling, but also on:

Deep Exploratory Data Analysis (EDA)
Domain-driven feature engineering
Handling class imbalance
Comparing multiple models using advanced evaluation metrics
📊 Dataset
The dataset contains millions of transaction records (~5M rows)
Target variable:
isFraud → 1 (Fraud), 0 (Legitimate)
Additional fields include:
Transaction type (TRANSFER, CASH_OUT, etc.)
Amount
Sender & receiver balances
Account identifiers

⚠️ The dataset is highly imbalanced, with fraud cases forming a very small percentage.

🔍 Exploratory Data Analysis (EDA)

Key insights:

Fraud is heavily concentrated in:
TRANSFER
CASH_OUT transactions
Fraudulent transactions often:
Have abnormal balance changes
Occur when sender balance becomes zero
Show inconsistencies in expected balance updates
Log transformation was used to analyze skewed transaction amounts

Visualizations used:

Transaction type distribution
Fraud rate by transaction type
Log-scaled amount distribution
Boxplots (Amount vs Fraud)
Correlation heatmap
⚙️ Feature Engineering (Strong Part of Your Project 🔥)

You created meaningful features based on financial logic:

errorBalanceOrig → mismatch in sender balance
errorBalanceDest → mismatch in receiver balance
amountToOldBalanceRatio → transaction size relative to balance
isZeroBalanceAfterTxn → detects full balance drain
isDestBalanceUnchanged → suspicious receiver behavior

👉 These features significantly improve fraud detection performance.

🧹 Data Preprocessing
Dropped irrelevant columns:
nameOrig, nameDest, isFlaggedFraud, type
Encoded categorical feature:
type → Label Encoding
Train-test split:
80% training / 20% testing
Stratified sampling (important for imbalance)
Feature scaling:
Applied StandardScaler for Logistic Regression
🤖 Models Implemented
1. Logistic Regression
Used class_weight='balanced'
Scaled features before training
2. Random Forest
n_estimators = 100
max_depth = 15 (to control complexity)
Handles imbalance using class weights
No scaling required
📊 Evaluation Metrics

Since the dataset is imbalanced, focus was on:

ROC-AUC Score
PR-AUC (Precision-Recall AUC) ⭐ (most important)
Precision
Recall
F1-Score
Confusion Matrix
📈 Model Comparison
Both models were evaluated on:
ROC Curve
Precision-Recall Curve
Random Forest performed better overall, especially in:
Capturing fraud cases (higher recall)
Handling nonlinear patterns
🔝 Feature Importance (Random Forest)

Top features included:

Balance error features
Transaction amount
Balance-related variables

👉 This confirms that engineered features added real predictive power

📁 Project Structure
fraud-detection-project/
│
├── fraud_detection_with_models.ipynb
├── README.md
└── fraud.csv (dataset)
🛠️ Tech Stack
Python
NumPy
Pandas
Matplotlib
Seaborn
Scikit-learn
▶️ How to Run
git clone https://github.com/your-username/fraud-detection-project.git
cd fraud-detection-project
pip install -r requirements.txt
jupyter notebook
💡 Key Learnings
Handling imbalanced datasets is critical in real-world ML
Feature engineering > model complexity
PR-AUC is more meaningful than accuracy in fraud detection
Tree-based models handle nonlinear fraud patterns effectively
🚀 Future Improvements
Hyperparameter tuning (GridSearchCV)
Try advanced models (XGBoost, LightGBM)
Deploy using Streamlit
Real-time fraud detection pipeline
