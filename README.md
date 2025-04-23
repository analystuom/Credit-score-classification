# Credit Score Classification

## Project Overview
This project implements a machine learning-based classification system to predict customer credit scores based on their banking details and credit-related data. The model categorizes customers into Good, Standard, or Poor credit score classes to support lending decisions.

## Problem Statement
A global finance company needed an automated method to classify customer credit scores using their banking and financial data. This classification system helps evaluate creditworthiness and improves decision-making in lending processes.

## Dataset Information
The dataset contains customer financial information with 28 features including:

- **Identifiers**: Customer ID, name, SSN
- **Demographics**: Age, occupation
- **Financial Data**: Annual income, monthly salary, bank accounts, credit cards
- **Credit Behavior**: Credit utilization ratio, credit history age, payment patterns
- **Loan Details**: Number of loans, loan types, payment history
- **Target Variable**: Credit score (Good, Standard, Poor)

## Key Insights from EDA
- Customers with Good credit scores typically have lower outstanding debt
- Good credit score customers often don't make minimum payments (likely paying more)
- Poor credit score customers generally have lower monthly incomes
- Most customers are classified with a Standard Credit_Mix
- Payment behavior strongly correlates with credit score classification

## Data Preprocessing
Several data quality challenges were addressed:

1. **Data Type Conversion**: Changed object types to categorical and appropriate numeric types
2. **Missing Value Treatment**: 
   - Replaced missing values with median for numeric features
   - Used mode imputation based on unique Customer_ID for categorical features
3. **Business Logic Alignment**: Ensured values in fields like Num_Bank_Accounts were consistent with business rules
4. **Categorical Encoding**: Converted categorical features to numerical format
5. **Outlier Handling**: Replaced outliers with Q1/Q3 values
6. **Correlation Analysis**: Removed highly correlated features (e.g., Monthly_Inhand_Salary due to 0.85 correlation with Annual_Income)
7. **Special Data Handling**:
   - Replaced placeholder values in Occupation column
   - Split Type_of_Loan into multiple binary columns

## Model Development
We tested multiple classification algorithms:

- Logistic Regression
- Gaussian Naive Bayes
- Decision Tree
- K-Nearest Neighbors (K=3, 5, 7)
- Random Forest (50 and 100 trees)
- Bagging methods
- Gradient Boosting
- XGBoost
- LightGBM

## Results
The Random Forest model delivered the best performance:

| Model | Accuracy | Poor Credit Score |  | Standard Credit Score |  | Good Credit Score |  |
|-------|----------|---------|--------|----------|--------|---------|--------|
|       |          | Precision | Recall | Precision | Recall | Precision | Recall |
| RF - 50 trees | 75% | 73% | 78% | 81% | 74% | 74% | 69% |
| RF - 100 trees | 75% | 73% | 78% | 81% | 74% | 75% | 69% |

Other ensemble methods (Bagging, Boosting) also performed well with accuracy scores ranging from 66% to 73%.

## Conclusions and Recommendations

1. **Model Selection**: The Random Forest model is recommended for implementation due to its superior performance in accuracy, precision, and recall across all credit score categories.

2. **Alternative Models**: Bagging and Boosting methods also demonstrated strong performance and could be considered as alternatives.

3. **Data Collection**: The company should enhance their data collection systems to ensure more complete information capture and improve model performance further.

4. **Feature Importance**: Focus on the most predictive features for credit scoring, which likely include payment behavior, credit utilization, and income levels.

## Setup and Usage

### Requirements
```
pandas
numpy
scikit-learn
matplotlib
seaborn
xgboost
lightgbm
```

### Installation
```bash
pip install -r requirements.txt
```

### Running the Project
```bash
python credit_score_classification.py
```

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Author
[Your Name]
