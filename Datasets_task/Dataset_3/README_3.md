# **Lumpy Skin Disease Prediction – Data Preprocessing & Exploratory Analysis**

## **1\. Dataset Source**

The dataset contains environmental, climatic, geographic, and land cover features associated with reported cases of Lumpy Skin Disease in livestock.

[https://www.kaggle.com/datasets/saurabhshahane/lumpy-skin-disease-dataset](https://www.kaggle.com/datasets/saurabhshahane/lumpy-skin-disease-dataset)

## **2\. Problem Statement**

The objective of this project is to:

Predict whether Lumpy Skin Disease (LSD) is present (`lumpy = 1`) or absent (`lumpy = 0`) based on climatic and environmental factors.

This is a **binary classification problem** where:

* Target Variable: `lumpy`  
* Input Features: Climate variables, land cover, elevation, and other environmental indicators.

The goal is to build a predictive model that can help identify high-risk environmental conditions for disease occurrence.

## **3\. Summary of Preprocessing Decisions**

The following preprocessing steps were performed:

### **1️⃣ Missing Value Handling**

* Columns `region`, `country`, and `reportingDate` had excessive missing values (\~21,000+), so they were removed.

  ### **2️⃣ Duplicate Removal**

* 608 duplicate records were identified and removed to avoid biased model learning.

  ### **3️⃣ Outlier Treatment**

* Outliers were detected using the **IQR (Interquartile Range) method**.  
* Instead of removing rows, outliers were **capped (Winsorized)** to:

  * Preserve valuable environmental extremes  
  * Avoid increasing class imbalance  
  * Maintain dataset size

  ### **4️⃣ Categorical Encoding**

* `dominant_land_cover` was label encoded.  
* Label Encoding was chosen because tree-based models handle ordinal encoded categories effectively.

  ### **5️⃣ Feature Scaling**

* Standardization (StandardScaler) was applied to numerical features.  
* Required for models sensitive to scale (e.g., Logistic Regression, SVM)..

## **4\. Key Insights & Observations**

* Climate variables such as temperature and precipitation show stable distributions after preprocessing.  
* Precipitation levels tend to be higher in disease-positive cases.  
* Temperature-related variables appear to influence disease occurrence.  
* Strong multicollinearity exists among temperature features (`tmn`, `tmp`, `tmx`).  
* Moderate correlation is observed between precipitation and wet days.  
* The target variable is highly imbalanced with significantly fewer disease cases.  
* Dominant land cover categories are unevenly distributed across observations.  
* Environmental factors show meaningful relationships with disease presence.  
* No direct evidence of data leakage is observed.  
* Climate variables are likely strong predictors of disease occurrence.

## **5\. Potential Next Modeling Steps**

* Class imbalance may bias the model toward predicting the majority class.  
* Multicollinearity may affect the stability of linear models.  
* Environmental data may contain natural noise that impacts precision.  
* Redundant climate features may increase model complexity.  
* High dimensionality from encoded categorical variables may increase overfitting risk.

* Model performance may not generalize well to unseen geographic regions.  
* Interaction effects between climate variables may not be captured by simple models.  
* Evaluation metrics must focus on recall and F1-score rather than accuracy.  
* Hyperparameter tuning will be required to prevent overfitting.  
* Choosing between interpretability and predictive performance will be necessary.

