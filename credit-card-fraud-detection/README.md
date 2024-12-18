# AIML
 
### Detecting Fraud transactions

#### Overview

This application is finding the insights from a bank's credit card transaction data and creating a datamodel to detect a transaction is fraudulent or legitimate. An effective model should be the one with reduced false negatives as this will minimize false flagging on legitimate transactions.

#### Rationale

There are many big and small fraudulent transactions happening nowadays. Many of us might have experience fraudulent  transaction on our own credit card. This affect banking institutions significantly as this involves substantial financial loss.Identifying fraudulent transactions  accurately will help financial institutions to prevent these significant money loss. Fraud detection will build trust customer confidence in financial institutions.

#### Understanding the Data

The dataset used in this analysis contains transactions from European credit cardholders collected in the year 2019.  It includes transaction data from a credit card company over the span of two days. 492 transactions out of 284,807 are labeled as fraud.Data set contains the result of a Principal Component analysis. There is no categorical features  and no null values. We do not have much information about the original features, as they have not disclosed due to the confidentiality nature of the data. Time and Amount fields were not transformed with PCA. 'Time” field contains the time elapsed between first transaction in the dataset and the current transaction.
 

#### Data Understanding

This data is collected from a Protuguese bank's directed marketing campaigns. Bank's own contact-center ran a total of 17 campaigns between May 2008 and November 2010. 

#### Understanding Task

Objective of this project is to analyze the data to find the characteristic of two types of labelled classes. And to create best model to predict a transaction is fraudulent or legitimate. 


#### Modeling
These datasets contains highly imbalanced classes so considering using decision trees and random forests. Decision Trees and RandomForest have the advantage of less sensitivity to class imbalances in the dataset dues to their hierarchical structure and ability to create separate path for minority classes.Logistic Regression alse used in this modeling because it can easily adap to class weights to improve performance of imbalanced data.
Simple models are built using Logistic Regression, Decision Trees, RandomForestClassifier. Feature importance is calculated after this. Finally these models are tuned by finding the best hypermarameters for each of these modeling and compared.

##### LogisticRegression : 
Class_weight 'None' and 'balanced' is used. 'balanced' class_weight effectively give importance to minority class. solver parameter used 'liblinear' and 'saga'. 'saga' is a variant of Stochastic Average Gradient and is more efficient for large datasets. It can handle multinomial loss and all penalities.l1(Lasso) and l2(Ridge)  penalty used, li can help identify the most important features for distinguising between classes, while l2 can prevent overfitting the class.'C': [0.001, 0.01, 0.1, 1, 10, 100] smaller c values increase regularization, that may generalized better but might underfit. Larger C values creates more complex models that fit training data more closely but might underfit.

##### DecisionTreeClassifier :
'max_depth': [3, 5, 7, 10, None] , here lower values can help overfitting to majority class on imbalanced dataset , but complex patterns may not be captured. Higher values or 'None' allow deeper trees. 'criterion': ['gini', 'entropy'] : 'gini' might perform better when there is a significant imbalance , while entropy could be preferable for more subtile imbalances.'min_samples_split': [2, 5, 10] this determines the minimum number of samples required to split the samples. A lower value allow the tree to create branches for rare minority class instances, while higher value could prevent overfitting to noise in the majority class.


##### RandomForestclassifier :  
'n_estimators': [250, 500, 750] this denotes the number of decision trees used. Increased number of trees gives stronger ensemble, potentially improving model's ability to identify rare fradulent cases. 'criterion': ['gini', 'entropy'] function used to measure the quality of the split. Entropy is slightly more sensitive to imbalanced classes, potentially giving better results in some fraud detection scenarios. cv=3 means 3-fold cross validation. Model is trained with two foldes and validated to the thrid fold. 

#### Evaluation
ROC : ROC curve is  drawn calculating true positive rate and false positive rate at selected interval and graphing TPR over FPR. 
AUC : Area under the curve represents the probability of a randomly chosen positive and negative samples. A perfect model has the area under the curve of 1.0 because the TPR is 1 and APR 0
When false positives are costly, we prioritize minimizing the False Positive Rate (FPR), even if it results in a lower True Positive Rate (TPR). Conversely, if false positives are inexpensive, we focus on maximizing the True Positive Rate (TPR), even if it leads to a higher FPR. If the costs for false positives and true positives are equal, we aim for a point where the TPR and FPR are balanced.

ROC AUC score evaluates on all possible thresholds and this helps on the current modeling as we do not have an optimal threshold in hand. ROC AUC gives equal importance to both positive and negative class which is crucial for fraud detection. ROC curve provides a visual representation of models performance which makes it easier for comparing different models.

Precision : Precision ensures legitimate transactions are not mistakenly classified as fraudulent.
Recal : Recall ensures that actual instance of fraud transactions are not missed to detect.

Precision , Recal and FI score are calculated for each model.  Models can be fine tuned based on the buisness need using the Precision , Recal and FI score. Precision score can be used to reduce false negatives.Recal scoring can be used maximize the chance to find the fraud.F1 score gives a balance between Precision and Recall score. When making more informed decisions, the precision-recall trade-off helps tailor the model to specific business needs. This allows us to choose whether we should minimize false alarms or prioritize catching more fraud.
Permutation Importance is calculated on each model to evaluate the best feature from Models.


| Without Hyperparameter tuning            | With Hyperparameter Tuning                 |
 ----------------------------------------------------------------------------------------                                                         
| Model                  |ROC AUC score    | Model                   | ROC AUC score    |
|:-----------------------|:----------------|:------------------------|:-----------------|
| Logistic Regression    | 0.97098         | Logistic Regression.    | 0.97636          | 
| RandomForestClassifier | 0.96442         | RandomForestClassifier  | 0.99999          | 
| DecisionTreeClassifier | 0.89714         | DecisionTreeClassifier  | 0.91495          |


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
11. RandomForest classifier has given the best ROC AUC Score of 0.99 and an average Precision score of 0.88. 
12.  Most important features are V14, V4, V12, V10, V17 , V3 and V11.


#### Deployment : 
Here we will take the evaluation result and create a strategy for deployment. Deploying a machine learning model involves validating data,
features, model versions, infrastructure and pipeline integration.
Integration testing involves testing different components of the machine learning pipeline works together. This tests are executed continuously after any software or model version changes.

#### Monitoring and Maintenance:
Monitoring and Maintenance of the deployed model is an important process to make model a part of the day to day business. A well prepared maintenance strategy avoid incorrect results from the model.Logging helps monitor the quality of predictions and detect any decline in performance. Another quality check can be performed through user reports. Adding a feedback option in the application allows users to easily provide this information.

Models can quickly become outdated when trained on old data. To maintain their relevance, models need to be retrained with new data and deployed to production before they become stale. A workflow pipeline helps keep the machine learning model up to date in production. An automated pipeline collects new data, trains the model, validates it, and deploys the updated version to production.


#### Link to the ipynb file 

  [Click here](https://github.com/sajeenam/AIML/blob/main/credit-card-fraud-detection/fraud-detection.ipynb)



  