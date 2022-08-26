


# Auto Loan Default Detection

<p align="center">
  <img src = "https://i.kinja-img.com/gawker-media/image/upload/c_fit,f_auto,g_center,pg_1,q_60,w_965/69b08da5f2e3573b59a08fdf9c9b5280.jpg" width="500" height="320">
</p> 

## Elevator Pitch

I recently developed a machine learning tool with borrowers' background data for bankers/investors who concern about auto loan delinquencies. This classification tool allows us to identify a loan that will default 59% of the time.


## Business Understanding

Due to increased income mainly from stimulus check and supply chain shortages, demand for cars has been sky rocketing. The average auto loan balance exceeded $20,000, and consumers owed a total of 1.4 trillion on the vehicles they drive. High inflation and interest rates can increase delinquencies as auto loan delinquencies a concern as they hit highest level since 2007. <a href="https://www.cnbc.com/video/2022/05/20/auto-loan-delinquencies-come-into-concern-as-they-hit-highest-levels-since-2007-says-bankrate-coms-mcbride.html">(CNBC)</a> The lending party is at a loss when a borrower defaults on a loan. Even if the collateral is taken, the time and money spent to turn it into funds can leave the lender with a negative return.<a href="https://www.gdslink.com/credit-risk-management-process-best-practices-techniques/">(GDS)</a>



**Stakeholders**: A bank manager who wants to minimize the number of defaulted loans in his position



**Data Sources:** 
- Automobile Loan Default Dataset <a href ="https://www.kaggle.com/datasets/saurabhbagchi/dish-network-hackathon?select=Test_Dataset.csv">(kaggle)</a>


The data set consists of 121856 total rows of data. There are 39 columns of features, and the `Default` is our target variable, with a 0 representing a normal loan and a 1 representing a defaulted loan.

**The Task:** 

The goal of the problem is to predict whether a borrower will default on the vehicle loan payment or not. 

## Exploratory Data Analsysis.

We look at the distribution of several feature groups—for example, a) `Client_Education` b) `Client_Income`  and `Credit Amount`.

Higher level education level tends to have a lower default %.

![ed_level](https://user-images.githubusercontent.com/65572411/186773080-49b3672f-3dfc-4921-8a99-cf5ed5022fb5.png)


Both default and normal groups are dense at the region of credit amount = 100000 and income = 15000, so we can't identify if default status occurs more in that region. 

![kds_plot](https://user-images.githubusercontent.com/65572411/186773069-ea2f8c1d-65b2-4a99-bed4-397b32107aaa.png)


## Data Processing:

Data cleaning
- Outlier Removal    
- Missing Value

Train-Test split and Pipeline

A 75%-25% train-test split and 5-Fold validation was implemented for the data. 

Pipeline
Set a preprocessing pipeline and a modeling pipeline. SMOAT doesn't have the fit_transform function in the sklearn pipeline, so we use two different pipelines, one for preprocessing and one for modeling.    

## Modeling:
    
The primary metric for assessing model performance was F1 score. F1 Score is the harmonic mean of Recall and Precision. However, we also considered the recall score (ratio of # of predict default to the total number of default) since the context of false negative default loans far outweigh the significance of accuracy for the purposes of this business problem. 
    
The modeling process consisted of an iterative approach of attempting to build upon the previous best model. Training set data were fit into each respective model with validation performed to gauge performance on the testing data. A baseline model consisting of a simple dummy classifier was instantiated as a benchmark. 






## Evaluation

**Model Performance:**

![summary](https://user-images.githubusercontent.com/65572411/186773225-c32480c3-3435-4f6b-8042-0e548db49a9c.PNG)

Most of our models have an F1 score of around .2. The results are far from the perfect F1 score of 1. 

Specifically, we determined our best model, the logistic regression model, compared to the other models because it has a higher recall score, a 59% recall. However, the poor performance of precision and drop the F1 score to 19%. However, even if logistic regression has a slightly lower F1 score, we still choose it to be our best model because stake holder's priority is to minimize the number of default loans. Hence, the regression model is chosen.


![logistic_regression](https://user-images.githubusercontent.com/65572411/186773049-65598160-c9df-49aa-a1ae-f525198cca75.png)


![RF](https://user-images.githubusercontent.com/65572411/186773036-9569ef07-fe3c-48e7-b6cc-cfadc6329ea8.png)
## Feature Importance

Two significant features for the logestic regression model were the `Loan_contract_type_cl` and `Client_Income_Type_Retired` variables. The cash loan type is different than the typical auto loan type as the borrower receives cash while the retiree doesn't have a regular income. We may want to see if they have additional risk for these two variables.


![wright](https://user-images.githubusercontent.com/65572411/186773163-6da465cb-209e-4757-a351-25374c52cfdd.png)


## Recommendations

- Professional Insight: We would appreciate some professional insight to better feature selection and improve our model performance.

- Further investigation on loan type: We should examine to see if `Loan_contract_type_cl` and `Client_Income_Type_Retired` carry more risk of default. 

- Accuracy is still important: The model's accuracy is still a vital metric, even if we focus on the recall and precision score. For example, the logistic regression model would be functional if it didn't produce so many false positive results and predicted the true negative accurately. Then, we would have a higher precision score and F1 score.
 

- Examine payment history: This data set mainly consists of borrowers' background data. We want to investigate it further to see if the borrower's payment history pattern would change the prediction of this analysis. 


## Repository Structure

```
├── data
├── pdfs
├── .gitignore
├── README.md
└── Final_Project_5.ipynb
└── README.md
```




