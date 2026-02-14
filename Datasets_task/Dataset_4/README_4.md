# **King County House Price Prediction – Data Preprocessing & Exploratory Analysis**

## **Dataset Source**

The dataset used in this project is the **King County House Sales Dataset**, publicly available on **Kaggle**: [*https://www.kaggle.com/datasets/harlfoxem/housesalesprediction/data*](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction/data) It contains residential house sale records from **King County, Washington (USA)**, including Seattle and surrounding areas.The dataset includes 21,613 house sales with property characteristics such as size, quality, location, and price.

## **Problem Statement**

The objective of this project is to:

Predict the selling price of houses (`price`) based on property features.

This is a **Supervised Machine Learning – Regression problem**, where:

* **Input Features:** Bedrooms, bathrooms, square footage, grade, condition, location, etc.  
* **Target Variable:** `price` (continuous numerical variable)

The goal is to build a predictive model that accurately estimates house prices based on property attributes.

## **Summary of Preprocessing Decisions**

### **1️⃣ Data Cleaning**

* No missing values detected.  
* No duplicate rows found.  
* Dropped `id` column (unique identifier, not predictive).

  ### **2️⃣ Datetime Processing**

* Converted `date` column to datetime format.

* Extracted:

  * `sale_year`  
  * `sale_month`  
* Dropped original `date` column after extraction.

  ### **3️⃣ Outlier Handling**

* Significant right-skew observed in:  
  * `price`  
  * `sqft_lot`  
  * `sqft_lot15`  
  * `sqft_living`  
* Applied **log transformation** to reduce skewness.

* Did not remove extreme houses (luxury homes are valid business data).

* Converted `yr_renovated` into binary feature `is_renovated`.

  ### **4️⃣ Categorical Encoding**

* `zipcode` treated as categorical (One-Hot Encoding).  
* Ordinal features (`grade`, `condition`, `view`) retained as numeric.  
* `waterfront` kept as binary (0/1).

  ### **5️⃣ Multicollinearity Awareness**

* High correlation observed between:  
  * `sqft_living` & `sqft_above`  
  * `sqft_living` & `sqft_living15`  
* Noted for potential feature selection or regularization.

## **4\. Key Insights & Observations**

* House prices are right-skewed with most properties priced between $200K–$600K.  
* Living area (`sqft_living`) is the strongest predictor of price.  
* Construction quality (`grade`) shows a clear positive relationship with price.  
* Waterfront and view significantly increase property value.  
* Location (latitude) impacts pricing.  
* Strong multicollinearity exists among size-related features.  
* Luxury homes represent a small portion of the dataset.

## **Modeling Challenges**

* **Multicollinearity** between size-related features (`sqft_living`, `sqft_above`, `sqft_living15`) may affect Linear Regression stability.  
* **Skewed target variable (`price`)** requires transformation to meet regression assumptions.  
* **High-cardinality categorical feature (`zipcode`)** increases dimensionality after encoding.  
* **Non-linear relationships** between features and price may reduce performance of simple linear models.  
* Presence of **luxury property outliers** can influence error metrics.

## **Potential Next Modeling Steps**

* Start with **Linear Regression** as a baseline model.  
* Apply **Ridge/Lasso Regression** to handle multicollinearity.  
* Train **Random Forest or Gradient Boosting** for better non-linear modeling.  
* Evaluate using **R², RMSE, and MAE**.  
* Perform **feature importance analysis and hyperparameter tuning**.

