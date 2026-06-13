# Telecom Customer Churn Prediction

> End-to-end machine learning pipeline predicting telecom customer churn to optimize retention. Leverages SMOTE for class balancing and 5-Fold Cross-Validation. Compares Random Forest, XGBoost, and a custom Keras/TensorFlow ANN. Includes a serialized model for real-time customer risk scoring.

## Project Overview
Customer retention is a critical KPI for telecommunications operators, as acquiring a new customer is significantly more expensive than retaining an existing one. This project leverages both traditional Machine Learning and Deep Learning to predict customer churn based on account information, demographic data, and service usage patterns. 

By accurately identifying high-risk customers, telecom providers can proactively deploy retention strategies to protect revenue.

## The Dataset
The project utilizes the **WA_Fn-UseC_-Telco-Customer-Churn dataset** (~7,043 rows, 21 features), which includes:
* **Demographics:** Gender, Age (Senior Citizen), Dependents.
* **Services:** Internet type, Tech Support, Streaming capabilities.
* **Financials/Account:** Contract type, Monthly Charges, Total Charges.

## Technical Pipeline

### 1. Data Cleaning & Preprocessing
* **Handling Missing Data:** Addressed hidden missing values (blank strings) in the `TotalCharges` column.
* **Encoding:** Applied Label Encoding to transform binary and multi-class text categorical data into machine-readable formats.

### 2. Class Balancing (SMOTE)
The original dataset suffered from severe class imbalance (~73% retained / 27% churned). I implemented the **Synthetic Minority Over-sampling Technique (SMOTE)** to synthetically balance the training data, preventing the models from developing a majority-class bias.

### 3. Model Engineering & 5-Fold Cross Validation
I built and evaluated four distinct algorithms using 5-Fold Cross-Validation to ensure robust, real-world performance:
* **Decision Tree** (Accuracy: ~78%)
* **Artificial Neural Network (ANN)** built with Keras/TensorFlow (Accuracy: ~77%)
* **XGBoost** (Accuracy: ~83%)
* **Random Forest** (Accuracy: ~84%) 

### 4. Model Selection & Insights
**The Random Forest** was selected as the final production model. 
* *Technical Insight:* The deep learning ANN underperformed compared to the tree-based models. This illustrates that for relatively small, highly structured tabular data, ensemble tree models (like Random Forest and XGBoost) are inherently more efficient and less prone to overfitting than neural networks.
* *Deployment:* The optimized Random Forest model and preprocessing encoders were serialized via `pickle` to act as the engine for a standalone predictive script.

## Key Business Insights
1. **The Premium Flight Risk:** Data density analysis revealed a massive cluster of customers paying between $70 and $90 per month. Because high revenue is concentrated here, predicting churn in this specific bracket is the highest business priority.
2. **Contract Vulnerability:** Customers on Month-to-Month contracts exhibit a drastically higher churn rate compared to those locked into one- or two-year commitments.
3. **Retention Drivers:** Customers who lack basic add-on services like "Tech Support" or "Online Security" are highly susceptible to leaving.

   git clone [https://github.com/](https://github.com/)pritam01729/Customer-Churn-Prediction.git
