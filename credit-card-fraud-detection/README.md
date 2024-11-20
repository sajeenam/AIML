# AIML
 
### Detecting Fraud transactions

#### Overview

This application is finding the insights from a bank's credit card transaction data and creating a datamodel to detect a transaction is fraudulent or legitimate. An effective model should be the one with reduced false negatives as this will minimize false flagging on legitimate transactions.


#### Understanding the Data

The dataset used in this analysis contains transactions from European credit cardholders collected in the year 2019.  It includes transaction data from a credit card company over the span of two days. 492 transactions out of 284,807 are labeled as fraud.Data set contains the result of a Principal Component analysis. There is no categorical features  and no null values. We don’t have much information about the original features, as they have not disclosed due to the confidentiality nature of the data. Time and Amount fields were not transformed with PCA. “Time” field contains the time elapsed between first transaction in the dataset and the current transaction.
 

#### Data Understanding

This data is collected from a Protuguese bank's directed marketing campaigns. Bank's own contact-center ran a total of 17 campaigns between May 2008 and November 2010. 

#### Understanding Task

Objective of this project is to analyze the data to find the characteristic of two types of labelled classes. And to create best model to predict a transaction is fraudulent or legitimate. 


#### Modeling

Simple models are built using Logistic Regression, Decision Trees, RandomForestClassifier. Feature importance is calculated after this. Finally these models are tuned by finding the best hypermarameters for each of these modeling and compared.

#### Evaluation

Precision , Recal and FI score are calculated for each model.  Models can be fine tuned based on the buisness need using the Precision , Recal and FI score. Precision score can be used to reduce false negatives.Recal scoring can be used maximize the chance to find the fraud.F1 score gives a balance between Precision and Recall score.
Permutation Importance is calculated on each model to evaluate the best feature from Models.

#### Findings

1. Data is Highly imbalanced, with only 492 records classified as fraud out of 284,807 transactions.
2. The data has undergone Principal component Analysis (PCA) and there are no null values.
3. Correlations between the features are not strong. However V2 and V5  show a strong negative correlation with “Amount” feature. V7 and V20 also show some correlation with Amount. 
4. Outliers are present in both Fraud and Non fraud classes. Outlier may represent unique characteristics, so they are not removed **
5. The highest number of Fraud transactions are found in the amount range 500-1000  which is 42% of the fraudulent transactions in this dataset.
6. 31 % of fraudulent transactions fall within the amount  range 1000-5000
7. V4 and V11 exhibit distinct distributions for fraud and non-fraud classes. V1, V2, V3, V10 shows distinct profiles, while V25, V26, V28 have similar profiles for fraud and non-fraudulent transactions. 
8. SMOTE is used  address the class imbalance problem.
9. Models are created using LogisticRegression , DecisionTreeClassifier and RandomForestClassifier. Hyper parameter tuning is done and it is found that RandomForestClassifier model has comparatively better result.
10. Model evaluation is performed using ROC AUC , which measures models ability to classify a transaction as fraudulent or  legitimate, regardless of their relative frequencies in the dataset.
11. RandomForest classifier has given the best ROC AUC Score of 0.98 and an average Precision score of 0.88. 
12.  Most important features are V14, V4, V12, V10, V17 , V3 and V11.




#### Link to the ipynb file 

  [Click here](https://github.com/sajeenam/AIML/blob/main/credit-card-fraud-detection/fraud-detection.ipynb)