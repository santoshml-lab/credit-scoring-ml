Credit Scoring Model — Evaluation Results

Project Overview

This project predicts whether a loan application will be approved using applicant financial and demographic information.

The dataset contains 5,000 records with 9 input features and one binary target variable, "LoanApproved".

Class Distribution

The target variable is imbalanced:

- Not Approved (0): 3,849 — 76.98%
- Approved (1): 1,151 — 23.02%

Because of this imbalance, accuracy alone was not used as the primary evaluation metric.

Train/Test Split

- Training samples: 4,000
- Testing samples: 1,000

The split was stratified to preserve the target-class distribution.

Models Compared

Three classification approaches were evaluated:

1. Logistic Regression
2. Class-Balanced Logistic Regression
3. XGBoost

Model Performance

Model| Precision| Recall| F1 Score| ROC-AUC
Logistic Regression| 0.7778| 0.7000| 0.7368| 0.9113
Class-Balanced Logistic Regression| 0.6131| 0.8957| 0.7279| 0.9110
XGBoost| 0.9444| 0.8870| 0.9148| 0.9287

Class Imbalance Handling

For the balanced Logistic Regression model, class weighting was used.

For XGBoost, the positive-class weight was calculated from the training data:

"scale_pos_weight = 3.343"

This gives additional importance to the minority class during training.

Final Model

XGBoost was selected because it provided the strongest overall balance across precision, recall, F1 score, and ROC-AUC.

Final XGBoost results:

- Accuracy: 0.962
- Precision: 0.9444
- Recall: 0.8870
- F1 Score: 0.9148
- ROC-AUC: 0.9287

Confusion Matrix

The XGBoost confusion matrix contained:

- True Negatives: 758
- False Positives: 12
- False Negatives: 26
- True Positives: 204

Error Cost Reasoning

A false positive means the model predicts that an applicant should be approved when the actual outcome is negative. In a lending context, this can create additional financial risk.

A false negative means the model predicts rejection when the actual outcome is positive. This can cause the lender to lose a potentially creditworthy customer.

Therefore, both error types matter. The preferred threshold should ultimately depend on the financial risk policy of the lending institution.

Feature Importance

The most influential XGBoost features were:

Feature| Importance
EmploymentType_Unemployed| 0.370615
CreditScore| 0.153175
EmploymentType_Self-Employed| 0.093623
Income| 0.078053
EmploymentType_Salaried| 0.052694
LoanAmount| 0.022359
City_New York| 0.022160
Education_PhD| 0.021979
Age| 0.021523
Gender_Male| 0.021511

Plain-Language Interpretation

Employment-related variables were the strongest predictive signals in this model, followed by credit score and income.

Feature importance shows how strongly the model relied on a feature for prediction. It does not prove that the feature causes loan approval or rejection.

Limitations

This is an educational machine learning project and should not be used directly for real-world lending decisions.

The dataset may not represent real lending populations, and model performance may change on external data. A production lending system would also require fairness testing, explainability, regulatory compliance, monitoring, and human oversight.

Conclusion

The project demonstrates an end-to-end credit scoring workflow covering preprocessing, class imbalance handling, model comparison, evaluation, error analysis, and feature interpretation.

XGBoost achieved the strongest overall performance among the evaluated models.
