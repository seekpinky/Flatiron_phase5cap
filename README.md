


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
- <a href ="https://www.kaggle.com/datasets/saurabhbagchi/dish-network-hackathon?select=Test_Dataset.csv">(kaggle)</a>


The data set consists of 121856 total rows of data. There are 39 columns of features, and the `Default` is our target variable.




**The Task:** 

The goal of the problem is to predict whether a borrower will default on the vehicle loan payment or not. 


#pt 1

#pt 2

## Data Processing:
The target variable identified for this analysis, and`Default` is our target variable.

Data cleaning
- Outlier Removal    
- Missing Value

Pre-Processing
A 75%-25% train-test split and 5-Fold validation was implemented for the data. 
Pipeline
- Set a preprocessing pipeline and a modeling pipeline. SMOAT doesn't have the fit_transform function in the sklearn pipeline, so we use two different pipelines, one for preprocessing and one for modeling.    

    
## Modeling:
    
The primary metric for assessing model performance was F1 score. Models will be judged mainly based on their F1 Score. F1 Score is the harmonic mean of Recall and Precision. However, we also considered the recall score (ratio of # of predict default to the total number of default) since the context of false negative default loans far outweigh the significance of accuracy for the purposes of this business problem. 
    
The modeling process consisted of an iterative approach of attempting to build upon the previous best model. Training set data were fit into each respective model with validation performed to gauge performance on the testing data. A baseline model consisting of a simple dummy classifier was instantiated as a benchmark. 
    
    ![p5_logisitc regression](https://user-images.githubusercontent.com/65572411/186772366-015dcb9d-cc5e-4951-aa3d-6e2433060476.png)



## Evaluation

**Model Performance:**

Most of our models have an F1 score of around .2. The results are far from the perfect F1 score of 1. Therefore, we select the logistic regression model compared to the other models because it has a higher recall score with a slightly lower F1 score. 

Specifically, we determined our best model, the logistic regression model, compared to the other models because it has a higher recall score, a 59% recall. However, the poor performance of precision and drop the F1 score to 19%. 





**Recommendations:**

-Need some insight from other banker's to have a better feature selection.

-Further examine to see if Loan_contract_type_cl, and Client_Income_Type_Retired carry more risk of default. 

- Examine with payment history:This data set mainly consists of borrowers' background data. We want to investigate it further to see if the borrower's payment history pattern would change the prediction of this analysis.


## Repository Structure

```
├── images_presentation
├── pdfs
├── .gitignore
├── Image Classification - Binary.ipynb
└── Final_Project_5.ipynb
└── README.md
```




