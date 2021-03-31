
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

## Exploratory Data Analysis:
In the EDA I tried to get an overview of the data.  
That includes the structure, missing values and the relationship between the variables.

Here are some facts about the data:  
* imbalanced data set (ca. 4000 data points labeled as "no" and only around 500 labeled as "yes")  
* average age of clients is 41  
* ca. 85 % of Clients who signed a term deposit were single or divorced
* nearly no correlation between the variables  


![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/Correlation_Matrix.png)
![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/PairPlot.png)
## Model Comparison:

First, I transformed the categorical variables via OneHotEncoder. I also split the data into train and tests sets with a test size of 10%(due to the fact of less data with "yes"-label).


For this project, I assumed, that it is important for the marketing campaign to contact as many people as possible who are willing to sign the term deposit.   
Regarding the confusion matrix, I wanted to reduce the false-negative rate. 

![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/confusion_matrix_raw.png)(1)


In other words: I identified the model with the highest proportion of correctly identified actual posivites.  


So I compared the different models on the recall score.  

![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/recall.PNG)  

To have meaningful outcomes I used the SMOTE-technique to oversample the training data, because of the imbalanced data. Then I cross-validated the different methods and compared their recall score and fit time.  

![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/Models.PNG)  

The best model based on recall was the **Logistic Regression**.


 
## Hyperparameter Tuning:

For the hyperparameter tuning I used GridSearchCV to improve the recall score.   
Before hyperparametertuning the recall score was around 23 % for thes "yes"-labeld data.  
After tuning my model, it was able to predict 37/52 Clients who were willing to sign the term deposit (71 % recall).  
This is an improvement of 48 % compared to the untuned model.

![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/AUC_opt.png)
![](https://github.com/Reik96/Bank_Marketing_Project/blob/master/images/Confusion_Matrix_opt.png)   

The tradeoff by improving the recall is the reduced precision. Which leads to the fact, that more Clients who are labeled "yes" are actually "no".  


## Further Steps:  

Currently my model can predict around 71 % of Clients who are willing to sign the term deposit as such.  
To improve the model more data of clients with the label "yes" is necessary.  
The EDA revealed a lot of information about the clients. In addition to the machine learning model, the marketing department could adjust their campaigns with the current information (e.g. determine the target group).  

Furthermore, I have to admit that there are certainly still many things that I could have examined and included. Nevertheless, I am satisfied with my first machine learning project and would be happy to receive feedback, criticism and further suggestions.






















## Resources:
* https://www.kaggle.com/janiobachmann/bank-marketing-campaign-opening-a-term-deposit (inspiration on how to compare different models and plotting ROC)
* https://kiwidamien.github.io/how-to-do-cross-validation-when-upsampling-data.html (explanation on how to use imbalearn.pipeline)
* https://archive.ics.uci.edu/ml/datasets/Bank+Marketing (UCI Bank Marketing Data Set)
* (1) https://towardsdatascience.com/demystifying-confusion-matrix-29f3037b0cfa (Image of the confusion matrix)
