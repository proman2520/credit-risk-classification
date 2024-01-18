# credit-risk-classification
In this repository, you can find the report template, the lending data .csv (77536 observations), and the Jupyter Notebook (credit_risk_classification.ipynb) where the supervised testing happened. The following is a detailed report on the results of the models' supervised learning.

# Module 12 Report

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:
* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

The dataset, a .csv of length 77536, was comprised of 75036 low-risk/healthy loans (0) and 2500 high-risk loans (1). Each loan had eight different attributes affixed to it, though the goal of the testing was to create a model that could accurately predict loan status. First, the dataset was split into training and testing sets using the scikit-learn library. Using the TRAINING set, a rudimentary logistic regression model was built using the LogisticRegression module and method, which was then applied to the TESTING dataset. Under the results header, the classification report results can be found.

Next, using the RandomOverSampler module from the imbalanced-learn library, the training dataset was resampled. Each type of loan, low and high-risk, were assigned 56277 generated observations. Then, a second LogisticRegression model, classifier, was built to serve the same purpose as the first: test the model's accuracy for predicting loan status. The classification report results can be found below, where both models are contrasted against one another.

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.
* Machine Learning Model 1:
  * Accuracy: 94%
  * Precision: 93% Average | 100% in low-risk loans, 87% in high-risk loans
  * Recall: 95% Average | 100% in low-risk loans, 89% in high-risk loans

* Machine Learning Model 2:
  * Accuracy: 100%
  * Precision: 93% Average| 100% in low-risk loans, 87% in high-risk loans
  * Recall: 100%

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

In terms of raw accuracy, the model based on the resampled data (No. 2) performed better. However, in the confusion matrices of the models, Model 1 had 80 false positives and 67 false negatives, while Model 2 had 91 false positives and only 2 false negatives. In summary, Model 2 had slightly more false positives but much fewer false negatives. This means that while model 2 was an improvement, they both could be useful under different circumstances. If a bank desperately wants to avoid misidentifying a high-risk loan as low-risk, model 1 worked better. If a bank recognizes the implicit costs of identifying low-risk loans as high-risk and wants a stronger overall accuracy, model 2 was better. Both scored under 90% in accurately predicting high-risk loans.