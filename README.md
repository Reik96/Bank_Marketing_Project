
# Binary Classification for Bank Marketing


## Project Overview:

* Performing an EDA on the UCI Bank Marketing data set
* Handling an imbalanced data set
* Comparing different machine learning models 
* Optimizing a logistic regression model using GridSearchCV


## Introduction:

In the following project, I worked on the well known "Bank Marketing" data from the UCI Machine Learning Repository. The goal was to build a model for the binary classification problem within this data set.  
I am aware of the fact that there are many projects out there, who already dealt with this data, but since this is the very first project of mine, I wanted to get some hands-on experiences. 



### Input variables:

**bank client data:**

1 - age (numeric)  
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')  
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')  
6 - housing: has housing loan? (categorical: 'no','yes','unknown')  
7 - loan: has personal loan? (categorical: 'no','yes','unknown')  

**related with the last contact of the current campaign:**

8 - contact: contact communication type (categorical: 'cellular','telephone')  
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')  
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')  
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.  

**other attributes:**  

12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)  
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)  
14 - previous: number of contacts performed before this campaign and for this client (numeric)  
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')  

**social and economic context attributes**

16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)  
17 - cons.price.idx: consumer price index - monthly indicator (numeric)  
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)  
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)  
20 - nr.employed: number of employees - quarterly indicator (numeric)  

### Output variable (desired target):

21 - y - has the client subscribed a term deposit? (binary: 'yes','no')  

## Exploratory Data Analysis


![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/Correlation_Matrix.png)
![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/PairPlot.png)
## Model Comparison



## Hyperparametertuning


## Further Steps


















## Resources:
* https://www.kaggle.com/janiobachmann/bank-marketing-campaign-opening-a-term-deposit (inspiration on how to compare different models and plotting ROC)
* https://kiwidamien.github.io/how-to-do-cross-validation-when-upsampling-data.html (explanation on how to use imbalearn.pipeline)
* https://archive.ics.uci.edu/ml/datasets/Bank+Marketing (UCI Bank Marketing Data Set)
