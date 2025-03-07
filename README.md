# **Waze User Churn Prediction**

## **Overview**
This project aims to predict monthly user churn on the Waze app, a free navigation service used by drivers worldwide. Churn, in the context, quantifies the number of users who have uninstalled the app or stopped using it. The goal of this project is to build machine learning models that predict whether a user will churn based on historical user data. Various machine learning algorithms were trained, and the models were evaluated based on their recall scores. The best-performing model, Support Vector Machine (SVM), was selected for its ability to identify users likely to churn.

## **Data Understanding**
The dataset used in this project is called waze_dataset.csv, containing synthetic data created in partnership with Waze. The dataset consists of 14,299 customer records and includes features related to user activity, such as:

Number of drives: Total number of drives made by the user in a month.
Sessions: The number of app sessions per user in a month.
Activity days: Number of days the user has been active within a month.
Other features: Various other metrics that describe user behavior on the app.

The dataset is imbalanced, with a higher proportion of non-churn users compared to churn users. This imbalance was addressed using techniques such as class weighting and Synthetic Minority Over-sampling Technique (SMOTE) to balance the classes and prevent model bias.

## **Modeling and Evaluation**
Several machine learning models were evaluated for predicting churn, including:
* Logistic Regression
* Naive Bayes
* Random Forest
* AdaBoost
* XGBoost
* Support Vector Machine (SVM)
  
Given the imbalanced nature of the dataset, recall was chosen as the primary evaluation metric because it focuses on correctly identifying users who are likely to churn, minimizing the risk of false negatives (i.e., users who churn but are not identified by the model).

**Key Steps in the Modeling Process:**
1. EDA and Data Preprocessing: The data was analyzed, cleaned, and necessary feature engineering was performed.
2. Class Imbalance Handling: Techniques like SMOTE (Synthetic Minority Over-sampling Technique) and class weights were used to balance the dataset.
3. Model Training: Different models were trained using the preprocessed data.
4. Evaluation: The models were evaluated on a validation dataset and using recall as the promary metrics.
5. Prediction: The top-performing model was used to make predictions on the test dataset.

**Best Model Performance:**
The Support Vector Machine (SVM) model, which was trained using SMOTE to address class imbalance, achieved the highest performance. Its evaluation on the validation dataset yielded a recall score of 0.74 and a precision score of 0.32. When evaluated on the test set, the SVM model gave a recall score of 0.71 and a precision of 0.30.

## **Conclusion**
The churn prediction model for Waze was successfully built, and the best-performing model was the Support Vector Machine (SVM) with SMOTE. The model’s ability to accurately predict churn can help Waze target at-risk users with interventions to prevent churn. However, there is still room for improvement in precision, and further efforts could be made in hyperparameter tuning or incorporating more features to increase model accuracy.
