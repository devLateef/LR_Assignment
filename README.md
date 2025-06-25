Title: Predicting Loan Defaults Using Logistic Regression – A Case Study on SBA Loans
Introduction 
Sanctioning a loan is a critical decision in finance that requires a balance between risk management and profitability. While issuing loans to risky borrowers may result in defaults and financial losses, overly cautious lending can lead to missed opportunities. In this project, we utilize logistic regression to predict the probability of default using the Small Business Administration (SBA) Loans Case Dataset (1987–2014). This model can help lenders make informed decisions to minimize risk while supporting small business growth.
Data Preprocessing 
The SBA dataset contains 35 columns, including borrower information, loan terms, and financial figures. We undertook the following preprocessing steps:
•	Loading & Inspection: The dataset was loaded using pandas. Initial inspection showed missing values, date columns, and categorical data.
•	Handling Missing Data: Columns with over 50% missing values were dropped. According to the rule of thumb, the 5% missing values were also dropped.
•	Categorical Encoding: Categorical columns such as RevLineCr and LowDoc were encoded using One-Hot Encoding.
•	Standadization: Numerical columns such as DisbursementGross, GrAppv, and SBA_Appv were standardized using StandardScaler to ensure even contribution in the model.
•	Feature Selection: Columns like Name, State, City, Zip, LoanNr, ChkDgt, ChgOffPrinGr, daysterm, BalanceGross, ChgOffDate, xx, and MIS_Status were removed due to irrelevance, redundancy, not predictive, high cardinality, or potential leakage.
Exploratory Data Analysis
EDA was conducted to understand data patterns and relationships:
•	Default Distribution: Around 20% of loans defaulted, indicating class imbalance.
•	Loan Amounts: Defaulted loans showed slightly higher disbursement amounts on average.
•	Correlation: DisbursementGross, SBA_Appv, and Term showed potential correlation with default likelihood.
•	Visuals: Histograms and bar plots were used to visualize the distribution of key features and defaults by category (e.g., State, loan type).
Model Implementation
We implemented logistic regression from scratch using NumPy. The target variable was Default (1 = defaulted, 0 = not defaulted). The dataset was split into training and testing sets in an 80/20 ratio.
Model Evaluation
The logistic regression model was evaluated on the test set using the following metrics:
•	Accuracy: 89%
•	Precision: 91%
•	Recall: 93%
These metrics show that the model is fairly accurate and has good precision, meaning that when it predicts default, it's usually correct. Recall is moderate, indicating room for improvement in catching all defaults.
Interpretation & Report
•	Feature Importance: After standardization, feature coefficients indicated that:
o	Longer loan terms and larger SBA_Appv values increased the chance of default.
o	States like CA and loan types flagged as LowDoc=Y had slightly higher default risk.
•	Business Implications:
o	Lenders can flag high-risk loans based on size, term, and loan type.
o	Incorporating this model into underwriting tools can enhance credit decision-making.
o	Policymakers can analyze which programs (e.g., LowDoc) need more oversight.
Conclusion 
This case study demonstrated that logistic regression is a powerful and interpretable tool for predicting loan defaults. By preprocessing the SBA loan data, conducting exploratory analysis, and building a logistic regression model from scratch, we identified key risk indicators. Such models support better lending decisions, help minimize default rates, and ensure that support reaches viable small businesses.
