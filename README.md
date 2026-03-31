# Capstone-Initial-Report-and-Exploratory-Data-Analysis
Initial Report and Exploratory Data Analysis (EDA) for Capstone Assignment 20.1

### Project Title : Loan Default Risk Prediction Using Machine Learning

**Author** :
Kumar Ashesh

#### Executive summary
This project develops a predictive machine learning framework to identify high-risk borrowers and mitigate financial losses for lending institutions. It analyzes a dataset of over 148K records and does data cleaning, exploratory data analysis (EDA), feature engineering, and baseline modeling. Baseline Logistic Regression is build to identify potential defaulters as well as key risk drivers like loan-to-income ratio, credit score, and loan characteristics. The project demonstrates the power of combining traditional financial ratios (LTV, DTI) with modern ML techniques like SMOTE and Log Transformations to identify "at-risk" borrowers while maintaining regulatory transparency.


#### Rationale

Loan defaults are one of the most significant costs for financial institutions. Even a 1% reduction in the default rate can save a large bank millions of dollars.  Accurate prediction models can help lenders:
- Reduce financial losses
- Improve credit approval strategies
- Ensure regulatory compliance 
- Follow reponsible lending practices

Understanding the drivers of default also benefits regulators and borrowers by promoting transparency and fairness in lending systems.

#### Research Question

Can we accurately predict the likelihood of a borrower defaulting on a loan based on their financial characteristics (income, debt) and loan-specific attributes?

#### Data Sources

The dataset used in this project is sourced from Kaggle:
[Loan Default Dataset](https://www.kaggle.com/datasets/yasserh/loan-default-dataset)

This dataset contains approximately 148,000 records with features including:
- Borrower financial information (income, debt-to-income ratio)
- Credit attributes (credit score, credit type)
- Loan details (loan amount, interest rate, loan purpose)
- Target variable: Status ( 0 for No Default, 1 for Default).

#### Methodology

- **Exploratory Data Analysis (EDA):** Analyzed class imbalance (approx. 25% default rate), identified right-skewed income distributions, and visualized multicollinearity between loan amounts and property values.
- **Data Cleaning:**
Dropped irrelevant features to reduce complexity. Implemented median imputation for missing numerical values and "Unknown" labels for categorical gaps.
- **Feature Engineering:**
Applied Log Transformations (np.log1p) to income and loan features to normalize skewed data.
Capped LTV ratio to mitigate extreme nomalies.
- **Preprocessing Pipeline:** Utilized Scikit-Learn pipeline and ColumnTransformer for robust scaling (StandardScaler) and categorical encoding (One-Hot Encoding).
- **Modeling:** Established a baseline using Logistic Regression with class_weight='balanced' to handle the inherent class imbalance.
- **Imbalance Analysis:** Performed SMOTE analysis to enhance logistic regression baseline


#### Results

- **Baseline Performance:** The Logistic Regression model, enhanced with SMOTE, achieved an Accuracy of 81% and a Recall of 0.69. This means the model successfully identifies 69% of all actual defaulters, providing a solid foundation for risk mitigation.
- **Linear Ceiling**: Comparison between class_weight='balanced' and SMOTE yielded identical results (Recall: 0.69, F1-Score: 0.64). This indicates that the current limitation is not class imbalance, but the linear nature of the baseline model, justifying the move to non-linear models.
- **Key Risk Drivers**: Based on feature evaluation, Credit Type (EQUI) with coefficient 8.70 is identified as the strongest predictor of default. High Upfront Charges (0.92) and Negative Amortization (0.88) were confirmed as top-tier risk signals.
- **Evaluation Insights**: The Precision-Recall Curve revealed a "Safe Rejection Zone" where 45% of defaults can be caught with near-100% precision.


#### Next steps

- **Non-Linear Model Upgrade**: Implement non-linear models like Random Forest or XGBoost to capture complex feature interactions that the current linear baseline misses.
- **Hyperparameter Optimization**: Use GridSearchCV to fine-tune the model parameters to maximize Recall without sacrificing precision.
- **Threshold Tuning**: Perform SHAP and threshold tuning
- **Enhanced feauture analysis**: Include more features
- **Deployment**: Build a dashboard


#### Outline of project

- [Capstone EDA Jupyter Notebook](https://github.com/kumes121/Capstone-Initial-Report-and-Exploratory-Data-Analysis/blob/main/CAPSTONE_EDA.ipynb)
- [Capstone EDA Github Repo](https://github.com/kumes121/Capstone-Initial-Report-and-Exploratory-Data-Analysis/tree/main)

