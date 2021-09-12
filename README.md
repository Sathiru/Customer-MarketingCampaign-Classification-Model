# Customer-Marketing Campaign-Classification-Model

## Problem Definition:
The purpose of this classification model is to predict if the client will subscribe (yes/no) a term deposit (variable y).

## Purpose:
- Can be used in any financial service sector to support marketing campaign.

## Datasets:
**train.csv:** Each row represents an observation for each individual campaign and the customer response. The dataset contains 15 columns and 32950 observations.

## Feature Description:

**age:** numeric	age of a person

**job:** 	type of job ('admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')

**marital:**	marital status ('divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)

**education:**	('basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')

**default:**	has credit in default? ('no','yes','unknown')

**housing:** 	has housing loan? ('no','yes','unknown')

**loan:**		has personal loan? ('no','yes','unknown')

**contact:**	contact communication type ('cellular','telephone')

**month:**	last contact month of year ('jan', 'feb', 'mar', …, 'nov', 'dec')

**dayofweek:**	last contact day of the week ('mon','tue','wed','thu','fri')

**duration:**	last contact duration, in seconds . Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no')

**campaign:**	number of contacts performed during this campaign and for this client (includes last contact)

**pdays:**	number of days that passed by after the client was last contacted from a previous campaign (999 means client was not previously contacted)

**previous:**	number of contacts performed before this campaign and for this client

**poutcome:**	outcome of the previous marketing campaign ('failure','nonexistent','success')

**Target variable:** y	binary	has the client subscribed a term deposit? ('yes','no')

## Data Preprocessing:

**Cleaning and Explanatory Data Analysis**

> Checked for null values, no null values

> Checked for duplicate values, Deleted the 8 duplicated rows.

> Checked for the distribution of target variable, where the target variable is highly imbalance. 

![image](/images/Client_subscription_desc.png)  

The below table shows that the target variable contains the data with the ratio of 89% "NO" to 11% "Yes", which is highly imbalanced dataset. 

|  | Count | 	% |
| ---- | ----- | ----- |
| no |	29230 |	0.887317 |
| yes	| 3712 |	0.112683 |

> Performed subsetting of data to extract the data that has the target variable "yes" to conduct EDA.

> Performed explanatory data analysis to learn more about the relation between each feature and the target variable.

____________________________________________________
#### All categorical features versus target variable
_____________________________________________________

Below are the charts to describe the independent features in reference to the target variable "yes" who all accepted the subsription.
![image](images/features_Vs_target.png)

Above charts shows that *married* customer with *university or high school* degree are more likely to agree for long term deposit. Similarly,
campaigns conducted during *summer* months and *middle of weekdays* are comparatively effective.
There is an ananomous data element *unknown* in several features.

________________________________
#### Age Distribution
__________________________

![image](images/age.png)

* The data is right skewed to see extreme outliers 
* Undeserved age category to be less than 20 years or age older than 60.

______________________
#### Duration Distribution
_________________________

![image](images/duration.png)

* The duration seems to the right skewed with ouliers.
* The mean duration for a call is 180 mins.

_________________
#### PairPlot
_______________

Pairplot to describe the relation between the variables

![image](images/pairplot.png)

From pairplot, it shows that the duration and the campaign mostly focused on younger people and skewed down as the age goes up, as per the 
data description values (pdays=999) means was not contacted before - Ignoring that, whomever was contacted was done with in the last 30 days. 
In most cases the number of times contacted before a campaign was < 6 times.

_____________________
#### Correlation 
______________________

![image](images/corr.png)

There is no evidence of muticollinearlity of correlation > 0.9, whereas pdays and previous are negatively correlated with -0.73, which can be ignored as 999
in pdays has no value, which will be fixed.

> Handled ananomous data element ***unknown***, replaced the uknown to null.

> Dropped variable *default* - being a highly imbalanced feature doesn't provide much value to the model.

> Handled missing values generated due to ***unknown***, columns contained null values are 'job', 'marital', 'education', 'housing' and  'loan'. Filled the null 
> values by taking mode of each column. 

## Feature Engineering:

> Performed one-hot encoding for nominal categorical variable like 'marital', 'housing', 'loan', 'contact' and 'poutcome'.
> performed label encoding for 'month', 'weekday', 'job' and 'education'.

## Classification Model

### Model Evaluation Criteria and Metrics:

On any classification problem the main goal is to minimize the false positive(precision) and false negative(recall) rate.

**Model Performance Caveat:**

Classified as the customer will agree for the deposit term and the customer doesn't - Loss of resources - False Positive
Classified as the customer will not agree for the deposit term and the possibility he/she does - Loss of opportunity - False Negative
Both the classes are important in this model to minimize the resource spent and maximize the opportunity given in order to maximize the profit.

Metrics to satisfy our needs of measures are - **F beta score** ( where the threshold is set to 1(f1 score) as focusses on both recall and precision) 

__Created a baseline model using logistic regression with imbalanced dataset produced a F1_score of 39%__

**Logistic regression with imbalanced dataset** - Both F1 score and the average precision recall score is very poor -less that 40%. Lets see if the model performance can be improved by handling imbalanced dataset, Technique to use -

1. Undersampling - Deleted the majority cases to match with minority.
2. Oversampling - Create more data points on top of existing data points in order to attain balanced target data
3. Oversampling using SMOTE - Create more data points in reference with similar data points using KNN.

Here I used Oversampling with **SMOTETOMEK** technique.

> Generated a balanced dataset from SMOTETOMEK
  __Below table shows the target variable from original imbalanced dataset to after SMOTE technique__
  
  |  | 0 | 1 |
  | ---- | ----- | ----- |
  | Original | 21942 | 2764 |
  | SMOTE | 21785 | 16299 |
  
  
  




 
