# Credit Card Lead Prediction

## :memo: Description

- This is a classification machine learning problem to identify the customers of a mid-sized bank that could show a higher intent towards a recommended credit card 	:credit_card:.
- In this project we have combined the predictions made by **XGBOOST** and **LightGBM** using **Stacking**. 


## :hourglass: Dataset

The dataset **`train.csv`** is used for training. The train dataset had 2,45,725 records with 11 features.<br>
The dataset consisted the following attributes : 
- **ID** : Unique Identifier for a row
- **Gender** : Gender of the Customer
- **Age** : Age of the Customer (in Years)
- **Region_Code** : Code of the Region for the customers
- **Occupation** : Occupation Type for the customer
- **Channel_Code** : Acquisition Channel Code for the Customer  (Encoded)
- **Vintage** : Vintage for the Customer (In Months)
- **Credit_Product** : If the Customer has any active credit product (Home loan, Personal loan, Credit Card etc.)
- **Avg_Account_Balance** : Average Account Balance for the Customer in last 12 Months
- **Is_Active** : If the Customer is Active in last 3 Months
- **Is_Lead(Target)** : If the Customer is interested for the Credit Card (0 : Customer is not interested , 1 : Customer is interested)

## :page_with_curl: Technical Overview
The project has been divided into the following steps :
### 1. Exploratory Data Analysis
### 2. Data Cleaning
- The Missing Value in the **Credit_Product** column is imputed with **No_Info**
### 3. Feature Engineering
- The categorical features (Gender, Region_Code, Occupation, Channel_Code, Credit_Product, Is_Active) were **One Hot Encoded**.
### 4. Oversampling (Handling Class Imbalance in Target Feature)
- About **76.27%** customers are not interested in credit card, and about **23.72%** are interested in credit card. To address this imbalance Oversampling techniques like **SMOTE** is used.
### 5. Modelling and Hyperparameter Tuning
* In Modelling both LightGBM and Xgboost is used. 
* For combining the predictions made by XGBoost and Light GBM, stacking is used
* The models are tuned using Randomized Search CV
* To prevent overfitting 5 kfold cross validation was performed

### :open_book: [Approach Document.pdf](https://github.com/AbhishekGit-hash/Credit-Card-Lead-Prediction/blob/master/Approach%20Document.pdf)

## 📈 Modelling and Evaluation
* In this project **ROC-AUC score** was used as evaluation metric.
* The Xgboost model gave a ROC-AUC score of 0.879 while the LightGBM model gave a ROC-AUC score of 0.876 

## 	:clipboard: Results
### 1. Feature Correlations
**Age** and **Vintage** has highest correlation (__0.63__) in train dataset and (__0.62__) in test dataset. <br>
<img src="Visualizations/FEcorr.PNG" height="350" align="middle"><br>
### 2. Feature Importance
#### XGBoost
In the **XGBoost** model, the top 5 features of importance are : **Avg_Account_Balance**, **Vintage**, **Age**, **Is_Active_No** and **Credit_Product_Yes**.<br>
<img src="Visualizations/XGboost_FE.png" height="500" align="center"><br>
#### LightGBM
In the **LightGBM** model, the top 5 features of importance are : **Vintage**, **Age**, **Occupation_Other**, **Avg_Account_Balance** and **Occupation_Self_Employed**.<br> 
<img src="Visualizations/LightGBM_FE.png" height="500" align="center"><br>
