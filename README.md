TOPIC: Bank Marketing Campaign
PROBLEM STATEMENT:
The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. 
Often, more than one contact with the same client was required, to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.
The classification goal is to predict if the client will subscribe to a term deposit or not. (variable y)
Marketing campaigns are characterized by focusing on the customer needs and their overall satisfaction. Nevertheless, there are different variables that determine whether a marketing campaign will be successful or not. There are certain variables that we need to take into consideration when making a marketing campaign.
The dataset consists of 45211 rows and 17 columns.
The goal of our project is to build a model to predict whether the client is interested in subscribing for the term deposit or not.
Our model will help to predict the future as well.
DESCRIPTIVE DATA ANALYSIS:
Descriptive analysis is a method used in statistics and data analysis to summarize and describe the key features of a dataset. The goal is to provide a clear and concise overview of the data, helping to identify patterns, trends, and key characteristics. Descriptive analysis does not involve making inferences or drawing conclusions about a population; instead, it focuses on organizing and summarizing the available information
Our original dataset looks like this.  
 
Our dataset doesn't have any missing values.
Here is the information about our features and target variables.
Features:
age --> age
job --> type of Job
marital --> marital status
education --> highest education finished
default --> already has credit in default?
balance --> account balance
housing --> taken housing loan?
loan --> taken personal loan?
contact --> communication via...
day --> day of last contact
month --> month of last contact
duration --> duration of last contact
campaign --> number of contacts made to the client during the campaign
pdays --> number of days that passed by after the client was last contacted from a previous campaign (999 means client wasn't previously contacted)
previous --> number of contacts performed before this campaign and for this client
poutcome --> outcome of the previous marketing campaign
Target variable:
y --> has the client subscribed to a term deposit?
Statistical Parameters:
 
From the description of numerical features, it is clearly known that there are several outliers present in these values as the max value varies from the mean value.
Checking NULL values:
 

There is no missing values in this dataset.
Unique Values information:
 
In our dataset we have 77 unique values in ‘age’, 12 in ‘job’, 3 in ‘marital’, 4 in ‘education’, 2 in ‘default’, 7168 in ‘balance’, 2 in ‘housing’, 2 in ‘loan’, 3 in ‘contact’, 31 in ‘day’, 12 in ‘month’, 1573 in ‘duration’, 48 in ‘campaign’, 559 in ‘pdays’, 41 in ‘previous’, 4 in ‘poutcome’, 2 in ‘Target’.
Missing values and null value observation:
Job has 0.63% unknown value - drop unknown rows
Education has 4.11% unknown values - drop unknown rows
Contact has 13020 unknown value - replace unknown with cellular value.
Day and month have nan value = drop nan 
poutcome has 81.75% unknown values - replace unknown with others value.
Age has no null/missing value
Previous has no null/missing value
Marital has no null/missing value
After dropping all unknown values, the shape of dataset is 43193 rows and 17 columns.

Dropping the unnecessary columns:
Columns ‘day’ and ‘month’ are removed as both are unsuccessful.

DATA PREPROCESSING AND EXPLORATORY DATA ANALYSIS: 

Univariate analysis:
It is used to convert numerical variables into categorical variables with the help of binning technique through histograms.
The frequency balance for people with negative balance is more when compared with the people with positive balance. 
After completing the univariate analysis, we dropped those columns.

Multivariate analysis:

It is the process of exploring the relationship between multiple variables and the target variable.
Count plot to show the influence of age_categorical on target.
most no. of clients who haven’t subscribed for the term deposit fall under the categories of ‘Middle aged’ and ‘Young’
Count plot to show the influence of duration_categorical on target 
most no. of clients who haven’t subscribed for the term deposit are the ones who have been interacting with the institution for a short duration of time.
Countplot to show the influence of pdays_categorical on target.
most no. of clients who haven’t been subscribed for the term deposit are those who haven’t been contacted by the institution in previous days of the campaign.
Countplot to show the influence of campaign_categorical on target.
most no. of clients who haven’t been subscribed for the term deposit are those who have been contacted for less no. of time in this campaign.
Countplot to show the influence of balance_categorical on target.
most no. of clients who haven’t been subscribed for the term deposit are those who have low balance and negative balance in the Portuguese banking institution.
Countplot to show the influence of loan_categorical on target.
most no. of clients who haven’t been subscribed for the term deposit are those who haven’t taken any loan in this banking institution.

Countplot to show the influence of contact_categorical on target.
 most no. of clients who haven’t subscribed for the term deposit have rejected the term deposit on call in cellular phones.

LABEL ENCODING: 

We performed Label encoding to categoricl features to numerical features.
 
TRAIN-TEST SPLIT: 

Then we split the data into train and test in the ratio of 70: 30 ratios.

DATA STANDARDIZATION : 

Standardization of dataset is a common requirement for many machine learning techniques. They might behave badly if the individual features do not look more or less like the standard normally distributed data.
The Standard Scaler method is used to standardize the input values. StandardScaler() and fit_transform() functions are used here.

Model Observation Table:

First, we did model building on imbalanced data.
Then, we did model building on under sampled data and then the oversampled data to compare the models accuracy and get the best model.

We could observe the below data:

Accuracy was good for unbalanced data but the precision and the recall for the minority class was extremely less. We were more concerned about the precision value as we didn’t want to wrongly predict the possibility of a customer accepting a term deposit offer.

Then, we observed better precision values for the under sampled data. But oversampled data had the highest accuracy and good precision and recall values. This is because, most of the useful information was lost in under sampling.

ROC curve for Imbalanced data:

 <img width="360" alt="image" src="https://github.com/Sooriyavela/Bank_Marketing_Campaign/assets/144498455/df360cd9-8bb4-418b-9330-c9c8efd5217a">

ROC curve for undersampled data:
Model AUC score for Logistic regression: 0.6866852431019123
Model AUC score for Decision Tree: 0.7404533601933783
Model AUC score for KNN: 0.7444272897351095
Model AUC score for random forest: 0.7693391441973755

ROC Curve for oversampled data:

Model AUC score for Logistic regression: 0.6900541390150192
Model AUC score for Decision Tree: 0.8329986028641285
Model AUC score for KNN: 0.7895127488648271
Model AUC score for random forest: 0.8330422633601118


The Random Forest model's ROC curve is slightly better than the Decision Tree's ROC curve as it is closer to the top-left corner of the graph compared to the other Classifiers.
The AUC score for the Random Forest is slightly higher than that of the Decision Tree (0.8330 vs. 0.8329), indicating that both Random Forest and decision Tree perform slightly better in terms of distinguishing between the positive and negative classes based on the dataset.

We could observe that Duration was the most influential feature for Prediction in all the 4 models followed by poutcome.

Conclusion: 

We were able to observe that Both Random Forest and the Decision Tree Model performed better than the other 2 models and had the highest accuracy of 83% amongst other Models. Also, we could observe that Duration was the most influential feature for Prediction in all the 4 models followed by poutcome.
So, more the duration of the call, success or others in the poutcome, more the possibility of getting a term deposit offer from the customer.




![image](https://github.com/Sooriyavela/Bank_Marketing_Campaign/assets/144498455/8c7a688d-4a66-4e87-a7a6-6c2348ad87d1)
