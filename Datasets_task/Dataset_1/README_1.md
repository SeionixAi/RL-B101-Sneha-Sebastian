# **Waterborne Disease Dataset – Analysis & Preprocessing**

## **Dataset Source**

This dataset contains 10,000 structured patient records including demographic, laboratory, environmental, and hygiene-related features. It was provided as part of an academic lab dataset for disease prediction analysis. [*https://www.kaggle.com/datasets/srajaltiwari76/waterbrone-diease-based-on-medical-reports?resource=download*](https://www.kaggle.com/datasets/srajaltiwari76/waterbrone-diease-based-on-medical-reports?resource=download)

## **Problem Statement**

The objective of this project is to analyze patient clinical and environmental data to understand patterns associated with different diseases and prepare the dataset for supervised machine learning classification. The goal is to explore how factors such as age, gender, laboratory parameters, hygiene score, and water source contribute to disease occurrence and to build a predictive model in future stages.

## **Summary of Preprocessing Decisions**

Initial data understanding was performed using info() and describe() to examine data types and statistical summaries. The dataset contains 10,000 records with no missing values and no duplicate entries, so no imputation or removal was required. Target distribution was analyzed to understand class balance. Outlier detection was conducted for Age and WBC using boxplots, and extreme values were retained as they may represent real medical conditions. Categorical variables were encoded appropriately: Gender and Disease were label encoded, while Water\_Source was one-hot encoded. Numerical features were scaled to ensure uniform contribution across models and to support distance-based algorithms.

## **Key Insights & Observations**

Exploratory data analysis revealed meaningful patterns in the dataset. Age distribution shows a wide and balanced range of patients. WBC levels vary significantly across diseases, indicating differences in immune response. Hygiene score appears to differ among disease categories, suggesting environmental influence. Disease distribution varies across water sources, highlighting potential contamination risk factors. Gender-based differences were observed in some diseases. The correlation heatmap indicates moderate relationships among liver and kidney function markers, with no severe multicollinearity detected.

## **Potential Next Modeling Steps**

The next step is to split the dataset into training and testing sets and begin with baseline classification models such as Logistic Regression, Decision Tree, and KNN. More advanced models like Random Forest and Gradient Boosting can then be applied. Model performance should be evaluated using accuracy, precision, recall, F1-score, and confusion matrix. Feature importance analysis and hyperparameter tuning can further improve predictive performance.

