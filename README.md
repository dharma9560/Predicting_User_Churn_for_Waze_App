# **Waze User Churn Prediction**

## **Overview**
This project aims to predict monthly user churn on the Waze app, a free navigation service used by drivers worldwide. Churn, in the context, quantifies the number of users who have uninstalled the app or stopped using it. The goal of this project is to build machine learning model that predicts whether a user will churn based on historical user data. Various classification models were trained, and the models were evaluated based on their recall scores. The best-performing model, Support Vector Machine (SVM), was selected for its ability to correctly identify users likely to churn.

## **Data Understanding**
The dataset used in this project (`waze_dataset.csv`), contains synthetic data created in partnership with Waze. The dataset consists of 14,299 customer records and includes features related to user activity, such as:

Number of drives: Total number of drives made by the user in a month.
Sessions: The number of app sessions per user in a month.
Activity days: Number of days the user has been active within a month.

Refer to `meta_data_waze_dataset.txt` for detailed meta data.

The dataset is imbalanced, with a higher proportion of non-churn users compared to churn users. This imbalance was addressed using techniques such asassigning class weights and Synthetic Minority Over-sampling Technique (SMOTE) to balance the classes and prevent model bias.

## **Modeling and Evaluation**
Several classification models were evaluated for predicting churn, including:
* Logistic Regression
* Naive Bayes
* Random Forest
* AdaBoost
* XGBoost
* Support Vector Machine (SVM)
  
Given the imbalanced nature of the dataset, **recall** was chosen as the primary evaluation metric because it focuses on correctly identifying users who are likely to churn, minimizing the risk of false negatives (i.e., users who churn but are not identified by the model).

## **Key Steps**
1. **EDA and Data Preprocessing:** The data was analyzed, cleaned, and necessary feature engineering was performed.
2. **Class Imbalance Handling:** Techniques like SMOTE (Synthetic Minority Over-sampling Technique) and class weights were used to balance the dataset.
3. **Model Training:** Different models were trained using the preprocessed data.
4. **Evaluation:** The models were evaluated on a validation dataset and using recall as the primary metrics.
5. **Prediction:** The top-performing model was used to make predictions on the test dataset.

## **Results**

Following are the performance scores on validation dataset.

Note - In the table below:
* CW - Model uses class weights
* SMOTE - Model uses resampling using SMOTE
  
|    | Model Name                     |   Precision |   Recall |     f1 |   Accuracy |   ROC_AUC |
|---:|:-------------------------------|------------:|---------:|-------:|-----------:|----------:|
|  0 | Support Vector Machine (SMOTE) |      0.3174 |   0.7456 | 0.4452 |     0.6706 |    0.7    |
|  1 | Support Vector Machine (CW)    |      0.3107 |   0.7318 | 0.4362 |     0.6647 |    0.691  |
|  2 | Logistic Regression (CW)       |      0.3222 |   0.7199 | 0.4451 |     0.6818 |    0.6968 |
|  3 | Logistic Regression (SMOTE)    |      0.3327 |   0.7199 | 0.4551 |     0.6944 |    0.7044 |
|  4 | Random Forest (CW)             |      0.3072 |   0.6943 | 0.4259 |     0.6682 |    0.6784 |
|  5 | AdaBoost (CW)                  |      0.3265 |   0.6923 | 0.4437 |     0.6923 |    0.6923 |
|  6 | XGBoost (CW)                   |      0.3219 |   0.6844 | 0.4379 |     0.6885 |    0.6869 |
|  7 | Random Forest (SMOTE)          |      0.3048 |   0.6746 | 0.4199 |     0.6696 |    0.6715 |
|  8 | Naive Bayes (SMOTE)            |      0.3192 |   0.6371 | 0.4253 |     0.6948 |    0.6721 |
|  9 | AdaBoost (SMOTE)               |      0.3093 |   0.5069 | 0.3842 |     0.7119 |    0.6315 |
| 10 | XGBoost (SMOTE)                |      0.3121 |   0.426  | 0.3603 |     0.7318 |    0.6119 |
| 11 | Naive Bayes                    |      0.3233 |   0.3176 | 0.3204 |     0.7612 |    0.5872 |
| 12 | Baseline                       |      0.4545 |   0.0888 | 0.1485 |     0.8196 |    0.5329 |

## **Best Model Performance**
The Support Vector Machine (SVM) model, which was trained using SMOTE to address class imbalance, achieved the highest performance. Its evaluation on the validation dataset yielded a recall score of 0.75 and a precision score of 0.32. When evaluated on the test set, the SVM model gave a **recall score of 0.71** and a **precision of 0.30**. This represents **24x improvement** in recall compared to the baseline logistic regression model, which achieved only 0.03 recall. 

## **Feature Importance**

![image](https://github.com/user-attachments/assets/57200bd8-33da-4308-9288-606931914c1a)

We observe that customers with higher activity days and longer app usage tend to have lower likelihood of churning. In contrast, customers who engage in more frequent and longer drives per month are more likely to churn. This behavior suggests that their churn may stem from unmet needs within the Waze app, which doesn't fully cater to their specific requirements.

## **Conclusion**
The churn prediction model for Waze was successfully built, and the best-performing model was the Support Vector Machine (SVM) with SMOTE. The model’s ability to accurately predict churn can help Waze target at-risk users with interventions to prevent churn. However, there is still room for improvement in precision, and further efforts could be made in hyperparameter tuning or incorporating more features to increase model accuracy.
