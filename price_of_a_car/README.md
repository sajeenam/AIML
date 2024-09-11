# AIML
 
### What drives the price of a car?

#### Overview

This application is exploring a dataset from kaggle. The provided dataset contains 426 cars to ensure speed of processing. The original dataset in kaggle contains 3 million used cars. REport from this analysis will provide a clear recommendation to a client -- a used car dealership.

#### CRISP-DM Framework

Methodology used in this is CRISP-DM. This framework provides a framework for working through a data problem. Steps are documented below

#### Business Understanding

In a used car dealership, pricing the car correctly is crucial to maximizing profit from the sale. This profitability is influenced by accurately identifying the features and attributes that are in demand among buyers. Key factors include the car’s brand name, unique features, and any attributes that are not readily available in the market. Additionally, market trends and consumer preferences can significantly impact the sale of a car.

#### Data Understanding

We need to understand what are the available features in the dataset. Is there any missing values? If there are missing values , how relevant are those? Is there an option to replace empty cell using information from another cell or is it better to be dropped? Is any column identical to another column, if so can one of these be dropped.Is there any insignifficant fields which is not useful for modeling? What are the catogorical columns that can be transformed with proper encoding?

#### Data Preparations

Column Id and VIN are for identification purpose only, so this can be dropped. Region and State are almost identical columns here, so column Region can be dropped.Size column is missing 70% of its values.Model column contains vast amount sub category for manufacture columns and many of those contains junk values along with it, so dropping this column as well.

Year and manufacture data is missing for so many cars so decided to drop these records.

Columns year, odometer and price have got outliers when checked using plots and removed those outliers from these columns.

Rest of the missing value are replaced with 'other' / 'unknown_' or by getting the mean/mode of the column.

Columns year, odometer and price have got outliers when checked using plots so removed those outliers from these columns.

#### Modeling

Ridge Regression and Linear Regressions Models are built. Used a method to find best alpha for Ridge Regression. GridSearchCV has used to find best degree for PolynomialFeatures

#### Evaluation

Analysis is performed using CRISP-DM methodolgy and sometimes repeated steps for more data clarity and clear.There were some junk values and outliers in the data set, so revisited data preperation step to clean up those.The data set was huge and was heavy to do some of the modeling. So went back to change encoding to avoid additional column creation during transformation by onehot encoding and to remove some more outliers. I had to Restricted modeling with higher polynomial degree than 3 but calculated Ridge regression with different alpha values.GridSearchCV is done with polynimial degree as param grid and result showed degree 3 is better than degree 2. Ridge Regression and Linear Regression showed almost similar results. Important features shown from these modeling were same. 

Permutation Importance is calculated on each model to evaluate the results from Models.

#### Findings

Based on the clear analysis of the data and modeling these are the important factors that help to maximice price :

1. Newer vehicle - If the year of the car is latest then it yields more price.
2. Odometer showing lower reading - If the car is less driven since it is brought then it is better.
3. Cars with higher number of cylinders - The price is highers for cars with more number of cylinders.
4. Drive category -  forward or rear wheel drive are better to maximize the price.
5. Fuel - cars with gas has higher price value.
6. Transmission - cars with automatic transmission will yield more price.
7. Condition and Title status are the next two factors that affects the price.

#### Next Steps and Recommendations

1. We can improve modeling by creating more models and using different cross validation techniques.
2. Some modeling could not be acheived because of infrastructr limitations, this can be done using cloud or in a more capable machine.
3. More insights of the data can be gathered using plots and grouping.


#### Link to the ipynb file 

  [Click here](https://github.com/sajeenam/AIML/blob/main/price_of_a_car/prompt_II.ipynb)