
💳 Credit Scoring ML

A machine learning project for predicting loan approval using applicant financial and demographic information.

The project compares Logistic Regression and XGBoost, explicitly addresses class imbalance, and evaluates models using Precision, Recall, F1-Score, and ROC-AUC rather than relying on accuracy alone.

🎯 Project Objective

The goal is to build a binary classification model that predicts whether a loan application will be approved.

Target variable: "LoanApproved"

- "0" → Loan Not Approved
- "1" → Loan Approved

📊 Dataset

The dataset contains 5,000 applicants and 9 input features.

Features

- Age
- Income
- LoanAmount
- CreditScore
- YearsExperience
- Gender
- Education
- City
- EmploymentType

Target Distribution

- Not Approved: 76.98%
- Approved: 23.02%

This represents a clear class imbalance, so accuracy alone is not sufficient for evaluating the model.

🔍 Exploratory Data Analysis

The dataset was inspected for:

- Missing values
- Duplicate records
- Target-class distribution
- Numerical feature distributions
- Relationship between numerical features and loan approval

Missing values were found in:

- "Income" — 196
- "CreditScore" — 194
- "Education" — 198

There were no duplicate rows.

⚙️ Data Preprocessing

The preprocessing pipeline includes:

Numerical Features

- Median imputation for missing values
- Standard scaling

Categorical Features

- Most-frequent-value imputation
- One-hot encoding

The data was divided into:

- 80% training
- 20% testing

Stratified splitting was used to preserve the target-class distribution.

🤖 Models

Three approaches were evaluated:

1. Logistic Regression
2. Class-Balanced Logistic Regression
3. XGBoost

Class Imbalance Handling

The class imbalance was explicitly addressed using:

class_weight="balanced"

for Logistic Regression and:

scale_pos_weight = 3.343

for XGBoost.

This gives greater importance to the minority class without modifying the test set.

📈 Model Performance

Model| Precision| Recall| F1-Score| ROC-AUC
Logistic Regression| 0.778| 0.700| 0.737| 0.911
Balanced Logistic Regression| 0.613| 0.896| 0.728| 0.911
XGBoost| 0.944| 0.887| 0.915| 0.929

🏆 Final Model

XGBoost achieved the strongest overall performance.

- Accuracy: 96.2%
- Precision: 94.44%
- Recall: 88.70%
- F1-Score: 91.48%
- ROC-AUC: 92.87%

The model provides a strong balance between identifying approved applicants and limiting incorrect approvals.

🧮 Confusion Matrix

The XGBoost model produced:

- True Negatives: 758
- True Positives: 204
- False Positives: 12
- False Negatives: 26

Error Analysis

For a lending business, a False Positive can be particularly costly because it represents an applicant predicted as suitable for approval when the actual outcome is negative, potentially increasing financial risk.

A False Negative represents a potentially creditworthy applicant being rejected, which can result in lost business and customer opportunity.

The relative cost of these errors ultimately depends on the lender's risk policy.

🧠 Feature Importance

The most influential features in the XGBoost model were:

Feature| Importance
EmploymentType_Unemployed| 0.3706
CreditScore| 0.1532
EmploymentType_Self-Employed| 0.0936
Income| 0.0781
EmploymentType_Salaried| 0.0527

Plain-Language Interpretation

Employment-related variables were the strongest predictive signals in this model, followed by credit score and income.

Feature importance indicates how much the model relied on a feature for prediction. It does not prove that a feature causes loan approval or rejection.

🛠️ Technology Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn
- Google Colab
- GitHub

📂 Project Structure

credit-scoring-ml/
│
├── Credit.ipynb
└── README.md

🚀 How to Run

1. Clone the repository:

git clone https://github.com/santoshml-lab/credit-scoring-ml.git

2. Open "Credit.ipynb" in Google Colab or Jupyter Notebook.

3. Upload the required dataset.

4. Run the notebook cells sequentially.

⚠️ Limitations

This project is intended for educational and portfolio purposes.

The dataset and model should not be treated as a production-ready lending decision system.

Important limitations include:

- The dataset may not represent real-world lending populations.
- Feature importance does not establish causality.
- Model performance may change on external datasets.
- Real lending systems require fairness, explainability, regulatory compliance, monitoring, and human oversight.

📌 Conclusion

The project demonstrates an end-to-end credit classification workflow, including exploratory analysis, preprocessing, class-imbalance handling, model comparison, evaluation, error analysis, and feature interpretation.

Among the evaluated approaches, XGBoost achieved the best overall balance of Precision, Recall, F1-Score, and ROC-AUC.

This project demonstrates practical application of machine learning to a credit-risk prediction problem while emphasizing evaluation beyond accuracy.






