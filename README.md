# credit-risk-classification

## Overview of the Analysis

### Purpose of analysis

This dataset was analised in an attempt to automate the process of flagging high-risk loans by performing logistic regression. The financial information in the dataset was:

* Loan size
* Interest rate
* Borrower income
* Debt to income ratio
* Number of accounts
* Derogetory marks
* Total debt

Finally each loan was classified based on whether the loan was healthy or high risk. A quick manual examination of the data showed that most of the high risk loans have loan sizes <= $18,000, an intrest rate around <= 10%, debt to income ratio <= 60%, number of accounts <= 9, derogetory marks <= 2, and total debt <= $40,000. Having one or two of these high risk values wasn't nessiacarily a sign of a high risk loan, having multiple of these values does cause the risk to become a high risk loan.

### Stages of the machine learning process

This program was made firstly by importing the `lending_data.csv` into a pandas dataframe. This was then split into two seperate dataframes as the X and y axis; with the y axis containing the loan status classifier, and the X axis containing all of the financial data.

The data was then further split into a training and testing set at a 60:40 split. This split was used over the 75:25 split in an attempt to squeeze as much efficiency out of the dataset and machine learning model as possible.

The training data was then fit to a logistic regression model using the SAG (Stochastic Average Gradient) formula. The SAG formula wasn't chosen for any specific reason, instead a few variations of the logistic regression model was chosen and the most efficient model was chosen. The logistic regression model uses 250 max iterations in an attempt to get a more accurate model from a smaller dataset.

## Results

Out of 30,005 healthy loans, only 151 were incorrectly identified as high risk loans. The positive predictive value for this was 1 (30,005/(29854+99) = 1.0017). However out of the 1010 high risk loans, 99 were incorrectly labeld as healthy loans. The negative predictive value for this was lower at 0.95 (1,010/(911+151) = 0.951); while this is less than the healthy loans, this could still be considered acceptable to some as the precision for predicting a high risk loan is 86%.

## Summary

I would not recomend this sort of machine learning model for use alone without external oversite from trained individuals. High risk loans have a bigger risk of being incorrectly identified as a healthy loan than a healthy loan being identified as a high risk loan. While incorrectly identified healthy loans may cause customers some grief, they can always get the loans correctly identified by a staff member. If a customer gets a loan incorrectly identified as a healthy loan, when they are a high risk loan; there is the potential that they may be unable to pay off the loan before the error is identified.

An alternative model with more oversight would be a decision tree or a random forrest. I would recommend these types of models as this dataset has a low number of variables which decide whether or not the loan is high risk. A bonus to these two types of models is that they can be audited in the case you are finding certain loans being incorrectly identified.

## Files

* `credit_risk_classification.ipynb`: This is the main jupyter notebook which all the coding was done.
* `Resources/lending_data.csv`: This is the main dataset which the jupyter notebook is based off.