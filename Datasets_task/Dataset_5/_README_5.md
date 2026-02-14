# **Avocado Price Prediction – Regression Analysis – Data Preprocessing & Exploratory Analysis**

## **1\.  Dataset Source**

The dataset used in this project is the **Avocado Prices Dataset**, publicly available on **Kaggle [https://www.kaggle.com/datasets/neuromusic/avocado-prices](https://www.kaggle.com/datasets/neuromusic/avocado-prices)**

It contains weekly retail scan data of avocado sales across multiple regions in the United States from 2015 to 2018\.

The dataset includes:

* Average selling price  
* Total sales volume  
* Volume by PLU codes (4046, 4225, 4770\)  
* Bag size breakdown  
* Avocado type (Conventional / Organic)  
* Region information  
* Date and year

## **2\. Problem Statement**

The objective of this project is to **predict the AveragePrice of avocados** using available features such as:

* Sales volume  
* Avocado type  
* Region  
* Time-based variables

This is a **Supervised Machine Learning – Regression problem**, where the target variable is continuous.

## **3\. Summary of Preprocessing Decisions**

The following preprocessing steps were applied:

### **1️⃣ Data Cleaning**

* No missing values detected.  
* No duplicate rows found.  
* Removed irrelevant column (`Unnamed: 0`).

### **2️⃣ Datetime Processing**

* Converted `Date` column to datetime format.  
* Extracted `Month` feature to capture seasonality.

### **3️⃣ Outlier Handling**

* Volume-related features showed heavy right skew.  
* Applied log transformation (`log1p`) to reduce skewness and stabilize variance.

### **4️⃣ Multicollinearity Management**

* Strong correlations observed between:  
  * Total Volume and PLU-specific volumes  
  * Total Bags and bag-size components  
  * Derived time features (Month, Week, Quarter)  
* Redundant features were either removed or reserved for model-specific handling.

### **5️⃣ Categorical Encoding**

* Applied One-Hot Encoding for:  
  * `type`  
  * `region`  
* Prevented artificial ordinal relationships.

### **6️⃣ Feature Scaling**

* Applied Standardization for numerical features (for linear models).  
* Ensured compatibility with scale-sensitive algorithms.

## **4\. Key Insights & Observations**

* Most avocado prices range between **$1.0 and $1.8**, showing moderate right skew.  
* Organic avocados are consistently priced higher than conventional ones.  
* A negative relationship exists between total volume and price, reflecting supply-demand dynamics.  
* Clear seasonal patterns influence pricing.  
* Significant multicollinearity exists among aggregated volume features.

## **5\. Modeling Challenges**

* Multicollinearity among volume and aggregate features.  
* High skewness in numerical variables.  
* High-cardinality categorical feature (`region`).  
* Potential seasonal dependency in pricing.

## **6\. Potential Next Modeling Steps**

* Train baseline Linear Regression model.  
* Apply Ridge Regression to address multicollinearity.  
* Compare performance with Random Forest Regressor.  
* Evaluate using:  
* MAE (Mean Absolute Error)

* RMSE (Root Mean Squared Error)

* R² Score  
* Perform feature importance analysis.  
* Conduct hyperparameter tuning.

