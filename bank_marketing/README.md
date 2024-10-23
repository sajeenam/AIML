# AIML
 
### Comparing Classifiers on Bank Marketing data

#### Overview

This application is comparing performance of classifiers K Nearest Neighbor, Logistic Regression, Decision Trees, and Support Vector Machines. The dataset contains information from Bank Marketing campaigns to sell bank products.This dataset is taken from UCI Machine Learning Repository.


#### Understanding the Data

In a used car dealership, pricing the car correctly is crucial to maximizing profit from the sale. This profitability is influenced by accurately identifying the features and attributes that are in demand among buyers. Key factors include the car’s brand name, unique features, and any attributes that are not readily available in the market. Additionally, market trends and consumer preferences can significantly impact the sale of a car.

#### Data Understanding

This data is collected from a Protuguese bank's directed marketing campaigns. Bank's own contact-center ran a total of 17 campaigns between May 2008 and November 2010. 

#### Understanding Task

Objective of this task is to compare performance of models created using classifiers Logistic Regression, Decision Tree, K Nearest Neighbor and Support Vector Machines.


#### Modeling

Simple models are built using Logistic Regression, Decision Trees, K Nearest Neighbor and Support Vector Machines. Feature importance is calculated after this. Finally these models are tuned by finding the best hypermarameters for each of these modeling and compared.

#### Evaluation

Comparision of Train time , Train and Test accuracy gave a basic understanding of the model performance.Precision , Recal and FI score are calculated for each model.  Models can be fine tuned based on the buisness need using the Precision , Recal and FI score. Precision score can be used to reduce false negatives.Recal scoring can be used if buisiness wants reach maximize the chance to reach more customers and maximize service acceptance.F1 score gives a balance between Precision and Recall score.
Permutation Importance is calculated on each model to evaluate the best feature from Models.

#### Findings

Based on the clear analysis of the data and modeling, these are the important factors that help to maximice price :

1. Decision Tree model showed a best accuracy and it has taken the lease time to train.
2. Precision can be used to reduce false negatives. SVC model showed the best precision among all models with 0.93 for rejection(0) and 0.71 for acceptance (1)
3. Decision tree showed the best Recal score of 0.97 on rejection and a high of 0.52 on acceptance.
4. Decision tree model has the best FI score among all the models.

#### Next Steps and Recommendations

1. In this Bank Marketing data modeling, precision can be used fine tune the model. This will reduce false prediction on customer accepting a product. 
2. Some modeling could not be acheived because of infrastructur limitations, this can be done using cloud or in a more capable machine.
3. More insights of the data can be gathered using plots.
4. Furthur tuning of hyper parameters can be done based on the business need.


#### Link to the ipynb file 

  [Click here](https://github.com/sajeenam/AIML/blob/main/price_of_a_car/prompt_II.ipynb)