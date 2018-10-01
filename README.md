# Customer-Churn-Analysis

Methodology

In this project, we are performing Logistic Regression, Decision Tree algorithm and the Random Tree algorithm on the Telecom Dataset to predict the customer churn in the recent future. The first step would be to load the dataset and storing it in a vector. The dataset cleaning would be done after loading the dataset. The dataset would then be divided into the training and the test dataset which is a basic method to perform analysis on a dataset. Logistic regression technique would be applied on the train data and create the model. Then this model will be compared with the raw test data to predict the outcome. The next step would be applying the Decision Tree algorithm to take the decision of customer churn condition. After applying the Decision Tree, we will perform Random forest method which searches the random characteristics of the customers at the same time and obtain the best fit outcome for the customer churn situation. After performing all the three models, the final accuracy among all the three will be compared on the basis of the accuracy rate.

Project Analysis

First of all, we need some packages to be loaded for our project. The packages are as follows:
“plyr”, “ggplot2”, “caret”, “randomForest” and “party”. We can load these packages using “library()” command.
Importing the dataset
To perform Logistic Regression, Decision Tree, and Random Forest, we are going to use telecom dataset. 
We use “read.csv” to import the .csv file into the data frame we created called as “Telco”.
Exploring the Dataset
The “str” function gives the structure of the data. As seen above, there are 7043 observations (rows) and 21 variables (columns). We are going to predict customer churn, the “Churn” variable is our target variable. All the other variables will be used as object variables in our three models.
Cleaning the dataset
Data cleaning starts with dealing with the missing values.
The “sapply” function is used to find out the missing values in columns. After applying “sapply” function on “Telco”, we found out 11 missing values in “TotalCharges” column. We need to remove these missing values as it affects the efficiency of our models.
We also need to remove those variables as well which we do not need for the analysis, like “customerID”.
Logistic Regression
To fit the model into the dataset, first we need split our data into two parts. “train” set and “test” set. The “train” set consist of 70% of the “Telco” dataset and “test” set consist of 30%.
To split the dataset, we use “createDataPartition” function, and kept 70% of the Churn variable data in a vector “trn”.
Fitting the model
The next step is to fit the logistic regression model into our data. For this we use “glm” function.
“glm” function is used to generalize linear models, specified by giving a symbolic description of the linear predictor and a description of the error distribution.
After that we use “anova()” function to compare nested models. ANOVA is a statistical technique for investigating the data by comparing the means of the subsets of the data.
After analyzing the deviance table, we can see the drop-in deviance hen adding each variable one at a time. Adding “InternetService”, “Contract” and “Tenure” variables significantly reduces the residual deviance.
After that we need to evaluate the Logistic Regression Model predictive ability, it gives the accuracy of our Logistic Regression model, which comes out to be 0.7998. 
We use confusion matrix which calculates a cross-tabulation of observed and predicted classes with associated statistics. The function requires that the factors have exactly the same levels.
Decision Tree
After fitting the Logistic Regression Model, now we visualize the data using Decision Tree Model.
To visualize in a better way, we will use 3 variables “Contract”, “tenure” and “PaperlessBilling”.
We created a decision tree using a “ctree” function. The following is the decision tree visualization of dependent variable Churn and independent variables “Contract”, “tenure” and “PaperlessBilling”.

From the three independent variables we used in decision tree modeling, Contract comes out to be the most important variable to predict customer churn or not churn.
After analyzing the decision tree model, if any customer is in a one-year long contract and not using the PaperlessBilling, then this particular customer is unlikely to churn.
Apart from this, if any customer is in a month-to-month contract, and comes under the 0-12 month tenure, plus also using PaperlessBilling, then this customer is more likely to churn.
We are using the same decision tree model to create confusion matrix table and use it to make prediction. 
Now, we need to check the accuracy of our decision tree model, and which comes out be 0.7604.
The accuracy level is hardly improved. Let’s use Random Forest to check if we can do better or not.
Random Forest
“randomForest” function is used to create Random Forest Model.
The error rate is relatively low when predicting “No”, that means the prediction is pretty good when predicting “no”.
And the error rate is much higher when predicting “Yes”, that means the prediction is not good when predicting “Yes”.
Confusion Matrix requires the factors to have exactly the levels, for this we are converting “0” and “1” to “No” and “Yes” respectively.
Random Forest Error Rate
 
We plot our Random Forest Model, to determine the number of trees. The OOB error rate decreases as the number of trees increases. And then becomes almost constant. After 100 to 200 trees, we cannot able to decrease the OOB error rate.

Tune the Random Forest model to check the OOB error rate

We used “tuneRF” function to tune the Random Forest Model, after plotting the tuning Random Forest model, we can easily say that as the “mtry” increases, the OOB error rate decreases. 
Fitting the Random Forest Model again after tuning
The OOB Error Rate decreases to 19.7% from 20.11%.
Making predictions and confusion matrix again after tuning
The accuracy did not increase but the sensitivity improved, compared with the initial Random Forest Model before tuning.

Conclusion

The variables like the Tenure, Contract and PaperlessBilling are the important decision-making factor for the customer churn situation. Customers who are in a month-to-month contract, with PaperlessBilling and within 0-12 month tenure, are more likely to churn. Apart from this, customers who are in more than one-year contract and not using PaperlessBilling are unlikely to churn.
Fitting all the three models gives us the accuracy rate for each model. The accuracy rate of Logistic Regression Model is 79.98%, the accuracy rate of Random Forest before tuning comes out to be 79.36% and after we tune the Random Forest Model, the accuracy rate marginally increases to 79.74%. The accuracy rate for Decision Tree in all the three models comes out to be the lowest, i.e., 76.04%.
To conclude, we can say that the Logistic Regression and the Random Forest have provided better results and gives the better accuracy rate than the Decision Tree for the problem of predicting the Customer Churn in the future.
