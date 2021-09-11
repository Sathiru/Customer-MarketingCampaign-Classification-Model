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


 
