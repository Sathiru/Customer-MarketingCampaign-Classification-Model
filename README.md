# Customer-Marketing Campaign-Classification-Model

## Problem Definition:
The purpose of this classification model is to predict if the client will subscribe (yes/no) a term deposit (variable y).

## Purpose:
- Can be used in any financial service sector to support marketing campaign.

## Datasets:
**train.csv:** Each row represents an observation for each individual campaign and the customer response. The dataset contains 15 columns and 32950 observations.

## Feature Description:

age:numeric	age of a person

job: 	type of job ('admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')

marital:	marital status ('divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)

education:	('basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')

default:	has credit in default? ('no','yes','unknown')

housing: 	has housing loan? ('no','yes','unknown')

loan:		has personal loan? ('no','yes','unknown')

contact:	contact communication type ('cellular','telephone')

month:	last contact month of year ('jan', 'feb', 'mar', …, 'nov', 'dec')

dayofweek:	last contact day of the week ('mon','tue','wed','thu','fri')

duration:	last contact duration, in seconds . Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no')

campaign:	number of contacts performed during this campaign and for this client (includes last contact)

pdays:	number of days that passed by after the client was last contacted from a previous campaign (999 means client was not previously contacted)

previous:	number of contacts performed before this campaign and for this client

poutcome:	outcome of the previous marketing campaign ('failure','nonexistent','success')

Target variable:- y	binary	has the client subscribed a term deposit? ('yes','no')

## Data Preprocessing:

**Cleaning and Explanatory Data Analysis**

Checked for null values.

Checked for duplicate values, Deleted the 8 duplicated rows.

Checked for the distribution of target variable, where the target variable is highly imbalance. 

![image](/images/Client_subscription_desc.png)

|  | Count | 	% |
| no |	29230 |	0.887317 |
| yes	| 3712 |	0.112683 |


Performed explanatory data analysis to learn more about the relation between each feature and the target variable,

______________________
#### Salary versus jobType
____________________

![image](images/salary_vs_jobType.png)

The c-type job like CEO, CTO, CFO have higher average salary and the order goes down.

_________________
#### Salary versus degree
_________________________

![image](images/salary_vs_degree.png)

The higher the degree level the higher the salary is, eg Doctoral have higher salary though it all depends on field, industry and jobType, the visualization just implies how 
educational level infuence the salary.

__________________
#### Salary versus major
_______________________

![image](images/salary_vs_major.png)

Technical major have higher average salary

__________________________________
#### Salary versus industry
______________________

![image](images/salary_vs_industry.png)

Oil, web and finance industry seems to have higher salary

## Feature Engineering:

Performed one-hot encoding for nominal categorical variable like jobType, major and industry and performed label encoding for degree, used the educational level for labeling eventhough it is not a typical ordinal variable.

### Checked for correlation:

Most of the features are positively correlated with the target variable salary and they is no evidence of muticollinearlity of correlation > 0.9, whereas milesFromMetropolis is negatively correlated with Salary.

![image](images/corr.png)



 
