# 📊 Credit Card Behaviour Score: Model Development Documentation

## 🚀 Introduction
We participated in the **Machine Learning Hackathon** conducted by **IIT Guwahati** in collaboration with **IDFC Bank**. Our team developed a **Credit Card Behaviour Score Model**, a predictive model designed to estimate the likelihood of default on credit card accounts. This model helps in refining risk management strategies by identifying high-risk accounts and enabling proactive decision-making.

## 🎯 Problem Statement
The objective of this project was to create a machine learning model that predicts whether a credit card customer is likely to default. The model leverages historical customer data to generate predictions that can assist in minimizing portfolio risk.

## 📂 Datasets Provided
We received two datasets for model development and validation:
1. **Development Data** (96,806 records) with features including:
   - **Account Number**: Unique identifier for each customer.
   - **Bad Flag**: Indicates default status (1 for default, 0 for non-default).
   - Various attributes such as credit limits, transaction counts, delinquencies, and inquiry history.

2. **Validation Data** (41,792 records) similar to the development data but without the "Bad Flag".

## 🛠️ Approach to Model Development
### 1️⃣ Data Preparation
- **Handling Missing Values**: Imputed missing numeric values with mean/median and categorical values with mode.
- **Feature Encoding**: Applied one-hot encoding to categorical variables.
- **Feature Scaling**: Standardized numerical features to maintain consistency.
- **Class Imbalance Handling**: Adjusted class weights due to an imbalance between defaults and non-defaults.

### 2️⃣ Model Development
- **Model Choice**: Used **XGBoost**, a high-performance classifier for binary classification.
- **Configurations**:
  - **Objective**: `binary:logistic` for probability outputs.
  - **Evaluation Metric**: Log Loss to assess prediction quality.
  - **Hyperparameter Tuning**:
    - Learning Rate: `0.1`
    - Number of Estimators: `100`
    - Maximum Depth: `6`
    - Subsampling: `0.8`
    - Column Sampling: `0.8`
  - **Class Weighting**: Adjusted `scale_pos_weight` for class imbalance.

### 3️⃣ Model Evaluation
We assessed model performance using:
- **Log Loss**: Measures accuracy of predicted probabilities.
- **ROC-AUC Score**: Evaluates the ability to distinguish between defaults and non-defaults.
- **Precision-Recall Curve**: Important due to class imbalance, ensuring effective identification of defaults.

### 4️⃣ Predictions on Validation Data
- The trained model generated predictions for the validation dataset.
- Outputs included `account_number` and `predicted_probability`.
- Probabilities were rounded to three decimal places and stored in a CSV file (`validation_predictions.csv`).

## 🔍 Key Insights
- **Feature Importance**: Credit limits, historical delinquencies, and recent credit inquiries were highly predictive.
- **Handling Imbalanced Data**: Class weighting helped mitigate bias toward the majority class.
- **Data Quality**: Addressing missing values and outliers improved model performance.
- **XGBoost Efficiency**: Outperformed simpler models like logistic regression by capturing non-linear relationships.

## 📈 Results & Impact
The **Behaviour Score Model** proved to be an effective tool for predicting credit card defaults. Its insights can assist banks in:
- **Adjusting Credit Limits** for high-risk customers.
- **Enhanced Risk Monitoring** for potential defaulters.
- **Developing Retention Strategies** for borderline customers.

## 🔮 Future Enhancements
1. **Feature Engineering**: Incorporating transaction time-series trends for better prediction.
2. **Ensemble Learning**: Using stacking models to improve accuracy.
3. **Explainability**: Implementing SHAP values for better interpretability.
4. **Continuous Learning**: Periodic retraining to adapt to evolving customer behavior.

## 📤 Submission Details
The final predictions were submitted in `validation_predictions.csv` with the following format:
| Account Number | Predicted Probability |
|---------------|----------------------|
| 1234567890    | 0.872                |
| 0987654321    | 0.245                |

## 🙌 Acknowledgments
We thank **IIT Guwahati** and **IDFC Bank** for organizing the hackathon, providing us with valuable learning experiences in real-world risk modeling challenges. This project was a great opportunity to apply our machine learning skills in a practical setting.

---
**👨‍💻 Contributors:**
- Vinay Maguluri
- Sandeep Kommineni
- karthik Reddy

For any questions or collaboration, feel free to reach out! 📩

---
**📜 License:** MIT License

