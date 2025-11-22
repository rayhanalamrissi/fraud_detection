 Fraud Detection – Machine Learning Project

 📌 Project Overview
Credit card fraud is one of the most critical challenges in modern finance. Fraudulent transactions are rare (less than 1%) yet extremely costly. Detecting these anomalies in real time is essential for banking institutions to reduce financial losses, protect customers, and improve trust in digital payments.

This project explores a real-world credit card transaction dataset and applies machine learning techniques to classify fraudulent vs. non-fraudulent transactions. The goal is to understand transaction behaviors, detect key fraud patterns, and develop a predictive model to assist financial systems in flagging fraudulent activities.

---

 Objectives
• Analyze patterns and trends in transaction behaviors  
• Build a machine learning classifier to identify fraud  
• Evaluate model performance and ensure business usefulness  
• Provide actionable business recommendations  

---

Dataset Description
The dataset contains multiple types of transactions made with credit cards. Key columns include:

| Feature | Description |
|---------|-------------|
| `amount` | Transaction value |
| `type` | Transaction type (e.g., PAYMENT, TRANSFER, CASH_OUT) |
| `isFraud` | 1 = fraudulent transaction, 0 = legitimate |
| `oldbalanceOrg` | Balance before the transaction |
| `newbalanceOrig` | Balance after the transaction |
| `oldbalanceDest` | Receiver balance before the transaction |
| `newbalanceDest` | Receiver balance after the transaction |

Important observation:** Fraud is disproportionately associated with **TRANSFER** and **CASH_OUT** transactions.


Exploratory Data Analysis (EDA) – Key Insights

 Fraud Distribution
Fraud represents a very small percentage of all transactions (high imbalance).  
📌 This heavily impacts model training → Classifiers must be evaluated with precision/recall metrics, not only accuracy.

Transaction Types
Fraud mainly occurs when money is being transferred between accounts. FRAUD was almost nonexistent in these categories:
- PAYMENT
- DEBIT
- CASH_IN

  **Fraud Distribution**
<img width="407" height="325" alt="image" src="https://github.com/user-attachments/assets/ffd6a140-ead8-488b-ba21-2b5ffe1c05a7" />


**Fraud by Transaction Type**
<img width="403" height="323" alt="image" src="https://github.com/user-attachments/assets/3d937460-3a13-417b-b571-eaab156b3a39" />



📌fraudsters prefer moving money, not paying bills

 Amount, Balance Behavior
Fraud tends to show:
- Higher transaction amounts
- Suspicious sender account behavior where new balance ≈ old balance (implies fake account or emptying account)



 Machine Learning Model

 Model Used: Random Forest Classifier
Chosen because:
- It handles imbalanced data well
- Captures non-linear patterns
- Provides feature importance analysis

 Model Performance
| Metric | Result |
|--------|--------|
| **ROC-AUC** | **0.8975** |
| **Confusion Matrix** | Strong fraud detection with acceptable false positives |
| **Precision/Recall** | Optimized for fraud recall to reduce undetected fraud |

**Confusion Matrix**
<img width="316" height="275" alt="image" src="https://github.com/user-attachments/assets/227e945f-b812-4a81-80bb-3a264d83ea50" />

This means **the model correctly identifies fraudulent transactions with high confidence.**

Feature Importance Results
The most influential predictors were:
1. `amount`
2. `oldbalanceOrg`
3. `newbalanceOrig`
4. `type` (specifically TRANSFER + CASH_OUT)



 **Feature Importance**
<img width="559" height="276" alt="image" src="https://github.com/user-attachments/assets/ee2ef099-21b5-49a3-8c35-0e3a3094e62a" />



Fraud is strongly linked to large outgoing transactions that drain accounts.**



 Business Recommendations

 To improve fraud detection in real-world systems:

 1. Flag Large Transfer and Cash-Out Transactions
Especially when:
- New balance ≈ zero  
- Amount exceeds account activity baseline

 2. Track Balance Behavior Patterns
Unusual balance drops with abnormal frequency or amount should trigger alerts.

 3. Real-Time Fraud Scoring
Integrating a model like this into banking systems allows:
- Instant fraud flagging
- Dynamic risk scoring per user

4. Continuous Model Retraining
Fraud tactics evolve quickly. Continuous learning ensures sustained protection.

 Future Improvements
🔧 To improve performance further:
- Use XGBoost or LightGBM for higher accuracy
- Apply SMOTE or anomaly detection techniques for imbalance
- Add user behavioral history for personalized risk scoring

---

Skills Demonstrated
📌 End-to-End Data Pipeline  
📌 EDA & Data Cleaning  
📌 Classification with Machine Learning  
📌 Imbalanced Data Handling  
📌 Business-Oriented Interpretation  

---

 Conclusion
Fraud detection requires more than just building a model: it needs **data understanding + business awareness.
This project bridges analytical and strategic thinking to empower financial institutions with actionable insights and reliable fraud classification.

---

💛 *Thank you for reading! Feedback and suggestions are always welcome.*


