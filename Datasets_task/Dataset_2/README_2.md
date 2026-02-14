# **Bank Customer Churn Prediction – Data Preprocessing & Exploratory Analysis**

## **Dataset Source**

This dataset was obtained from Kaggle:  
 [*https://www.kaggle.com/datasets/chetanmittal033/bank-dataset-for-customer-churn-prediction*](https://www.kaggle.com/datasets/chetanmittal033/bank-dataset-for-customer-churn-prediction)

It contains 10,000 customer records with demographic, financial, and behavioral information. The target variable **Exited** indicates whether a customer has left the bank (1) or stayed (0).

## **Problem Statement**

The objective of this project is to analyze customer demographics and financial behavior to predict customer churn. Since retaining customers is significantly more cost-effective than acquiring new ones, identifying patterns associated with churn helps the bank proactively design retention strategies such as personalized offers, loyalty benefits, and improved services.

## **Data Overview**

The dataset consists of 10,000 records and 14 features, including numerical, categorical, and binary variables. Key financial indicators include CreditScore, Balance, EstimatedSalary, Tenure, and NumOfProducts. Demographic variables include Age, Gender, and Geography. The dataset contains no missing values and no duplicate records.

The average customer age is approximately 39 years, with credit scores centered around 650\. Around 20% of customers have exited the bank, indicating moderate class imbalance.

## **Summary of Preprocessing Decisions**

Initial data understanding was conducted using `.info()` and `.describe()` to assess feature types and distributions. RowNumber and CustomerId were identified as non-informative identifiers. No missing values or duplicates were found, so no imputation or removal was required.

Categorical variables such as Gender and Geography were encoded appropriately for modeling. Numerical variables were analyzed for distribution and scaled where necessary to support algorithms sensitive to feature magnitude. Target distribution analysis showed that approximately 20% of customers churned, suggesting potential need for imbalance handling during modeling.

## **Exploratory Data Analysis & Key Insights**

The overall churn distribution shows that most customers remain with the bank, but a significant minority (around 20%) have exited, which is meaningful from a business perspective.

Credit score distribution appears approximately normal, centered around mid-range values. However, boxplot comparison between churned and retained customers indicates that credit score alone is not a strong differentiator, as distributions overlap considerably.

Age distribution shows most customers fall between 30–45 years. Correlation analysis and distribution comparisons suggest that older customers are more likely to churn, with Age showing a positive correlation (\~0.29) with Exited.

Geography-wise analysis reveals that churn rates vary significantly across regions, with Germany showing relatively higher churn compared to France and Spain. This suggests possible regional service or competition differences.

Gender-wise analysis indicates that female customers show slightly higher churn rates compared to male customers.

Credit card ownership does not show a strong separation effect on churn, as both card holders and non-holders have exited customers.

The correlation heatmap shows that Age and Balance have moderate positive relationships with churn, while being an active member shows a negative correlation with churn, indicating that engagement reduces exit probability. No severe multicollinearity is observed among features.

## **Modeling Challenges**

The dataset exhibits moderate class imbalance (approximately 80% retained vs 20% exited). Some features such as CustomerId and RowNumber do not contribute to prediction and should be removed before modeling. Overlapping distributions for certain variables (e.g., CreditScore) indicate that nonlinear or ensemble models may perform better than simple linear models.

## **Potential Next Modeling Steps**

The next step is to split the dataset into training and testing sets and build baseline classification models such as Logistic Regression and Decision Tree. Advanced ensemble models like Random Forest and Gradient Boosting can be applied to capture nonlinear relationships. Performance should be evaluated using Accuracy, Precision, Recall, F1-score, ROC-AUC, and Confusion Matrix. Class imbalance handling techniques such as SMOTE or class weighting may further improve performance. Feature importance analysis will help identify the most influential drivers of churn for business decision-making.

