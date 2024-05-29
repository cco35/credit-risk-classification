# Credit Risk Analysis: Training ML Model to Classify Loans

## Overview of the Analysis

This report details the process of using historical lending data to train and evaluate a model's ability to predict the risk involved when granting loans to potential borrowers. The data used for this comprised of 77,536 rows and 8 columns namely; loan size, interest rate, borrower income, debt to income (ratio), num of accounts, derogatory marks, total debt, and loan status.
Here are some key statistical metrics for each of the columns used in training the model

| Metric             | Mean    | 50th Percentile (Median) |
| ------------------ | ------- | ------------------------ |
| loan_size          | 9805.56 | 9500.00                  |
| interest_rate      | 7.29    | 7.17                     |
| borrower_income    | 49221.95| 48100.00                 |
| debt_to_income     | 0.38    | 0.38                     |
| num_of_accounts    | 3.83    | 4.00                     |
| derogatory_marks   | 0.39    | 0.00                     |
| total_debt         | 19221.95| 18100.00                 |

The loan status column was the target variable for this model and 0 was used to classify lenders who were considered healthy (low-risk), and 1 was used for lenders who were high-risk. The data was split into training and testing subsets usign train_test_split before logistic regression was used to fit the model and then to make predictions regarding which category each lender fell into. Logisitic regression was used becasue it is good for binary classification tasks such as this one where the lenders are either going to be assigned a 0/1.

## Results

* Logistic Regression Model:
+ **Accuracy:** In this model, the accuracy refers to the overall prediction accuracy of the model i.e how many instnaces the model accurately predicted the loan status for. In the case of this model, it was 99% accurate (0.99). However it is important to acknowlwdge that there is a large class imbalance, and this accuracy score is heavily influenced by the perfect prediction of healthy loans.

+ **Precision:** The model's precision refers to how mnay instances the model predicts correctly of all those it identfies. In the case of healthy loans, the model's precision is 1.00 (100%) which means every loan indentified by the model as a healthy loan was healthy. 
Conversely, for high-risk loans the model's precision is 0.87 (87%) which means of all the instances identified by the model as high-risk, 13% (0.13) were false negatives. 

+ **Recall:** The model's recall is a measure of the completeness of the model's positive predicitions. In this case for healthy loans, the model perfectly indentifies each instance of a healthy loan within the dataset and this is represented by the 1.00 (100%) recall score.
For high-risk loan's 89% (0.89) of high-risk loans within the dataet were correctly identified by the model which represents an 11% (0.11) false negative rate.

## Summary

Based on the results obtained I would not recommend the model for use if a company wishes to to evaluate customer loan decisions. The reason for this decison is becasue the model's accuracy is heavily skewed by its ability to correctly identify healthy loans. 
If we take a look at the macro averages which are equally weighted across the two classes (healthy & high-risk loans) there precison, recall, and F1 score are all 0.94 which shows it is a god model, but this number is also heavily reliant on the heavy loan metrics.
While there are pros and cons to being able to prioritize identifying both healthy and high-risk loans, I believe there should be slightly more emphasis on correctly identifying high-risk loans. My rationale for this would be that high-risk loans being granted could have long lasting effects on a company as the default risk is much higher and this could lead to increased operational costs, financial strain on the business, and potential regulatory violations.

