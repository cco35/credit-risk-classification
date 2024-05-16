# Credit Risk Analysis: Training ML Model to Classify Loans

## Overview of the Analysis

This report details the process of using historical lending data to train and evaluate a model's ability to predict the risk involved when granting loans to potential borrowers. The dataset used comprised 77,536 rows and 8 columns: loan size, interest rate, borrower income, debt to income (ratio), number of accounts, derogatory marks, total debt, and loan status.

Here are some key statistical metrics for each of the columns used in training the model:

| Metric             | Mean    | Median |
| ------------------ | ------- | ------ |
| loan_size          | 9805.56 | 9500.00|
| interest_rate      | 7.29    | 7.17   |
| borrower_income    | 49221.95| 48100.00|
| debt_to_income     | 0.38    | 0.38   |
| num_of_accounts    | 3.83    | 4.00   |
| derogatory_marks   | 0.39    | 0.00   |
| total_debt         | 19221.95| 18100.00|

The loan status column was the target variable for this model, where 0 indicated healthy (low-risk) lenders, and 1 indicated high-risk lenders. The data were split into training and testing subsets using `train_test_split` before applying logistic regression to fit the model and make predictions regarding each lender's category.

## Results

### Logistic Regression Model:

- **Accuracy:** In this model, accuracy refers to the overall prediction accuracy, i.e., how many instances the model accurately predicted the loan status. In this case, it was 99% accurate (0.99). However, it is important to acknowledge that there is a large class imbalance, and the perfect prediction of healthy loans heavily influences this accuracy score.

- **Precision:** The model's precision refers to how many instances the model predicts correctly out of all those it identifies. For healthy loans, the precision is 1.00 (100%), indicating that every loan identified by the model as healthy was indeed healthy. Conversely, for high-risk loans, the precision is 0.87 (87%), meaning that 13% of the instances identified as high-risk were false negatives.

- **Recall:** The model's recall is a measure of the completeness of the model's positive predictions. The model perfectly identifies each instance for healthy loans, represented by the 1.00 (100%) recall score. For high-risk loans, 89% (0.89) of high-risk loans were correctly identified by the model, representing an 11% (0.11) false negative rate.

## Summary

Based on the results obtained, I would not recommend the model for use if a company wishes to evaluate customer loan decisions. The reason behind this decision is that the model's accuracy is heavily skewed by its ability to correctly identify healthy loans. If we look at the macro averages, which are equally weighted across the two classes (healthy & high-risk loans), their precision, recall, and F1 score are all 0.94, showing it is a good model, but this number is also heavily reliant on the heavy loan metrics.

While there are pros and cons to prioritizing identifying healthy and high-risk loans, I believe there should be slightly more emphasis on correctly identifying high-risk loans. My rationale for this would be that high-risk loans being granted could have long-lasting effects on a company, as the default risk is much higher, leading to increased operational costs, financial strain on the business, and potential regulatory violations.
