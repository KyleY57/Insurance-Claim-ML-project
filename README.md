# auto-claim-machine-learning-project
Problem:
A big predicament for larger firms is to make sure that insurance is profitable, therefore being able to predict the claim amounts before the event occurs would be imperative to understand for accurate loss reserving and risk selection. Using a dataset from Kaggle we will aim to predict insurance claim amount using a wide arrange of features. 


Action:

Feature preprocessing: 
Starting with 1000 observations and 40 features, we first need to look through any features that may not be necessary as well as missing data. This will make it easier to run the data through models, and dimensionality reduction will save computations that may not be needed. After inspection, removed features such as: IDs, hobbies of the insured, and authorities contacted, as well as features that may have multicollinearity such as: city, and location since we will be keeping the State. We did not have any missing data in this dataset, but if it did we could use mean or median imputing to simulate the missing point depending on what is missing.

We then categorize the features into respective data types such as: Numeric, categorical, as well as binary. We also have one ordinal feature, being education level which we will categorize accordingly to capture inherent hierarchy in policyholders. We will simplify the date of the event into the year it occured for generalization and comprehensivity. 

We then preprocess the features according to their datatypes, standard scaling for numeric data and onehotencoding for categorical and binary data.

Regression
Split data into training and test sets, then use cross validation on a variety of models. 
Dummy regression model, linear regression, and random forest. 

Preventing Information Leakage/Look-ahead Bias:
We will also run a separate regression using these models on a dataset that do not contain data we would not have before the incident. Such as: type of incident, severity, bodily injuries, and such. 

After getting subpar results, we will change our approach. We will create "bins" for the claim amount, and now aim to predict a range of values as a classification task rather than a regression. 

Now, due to the nature of classification, we will use slightly different models. Such as: Logistic regression, and random forest classifier. 


Result:

We were able to achieve a test score (R-squared) with random forest regression of 0.674 with the raw dataset. This can be interpretted as 67.4% of the variance in the target variable can be explained from our model (higher is better). After removing the features we would not know beforehand, the scores dropped significantly. Then switching to a classification task, we were able to marginally outperform the dummy classifier using random forest classification with a test score (R-squared) of 0.353 (35.3%). 

Final Remarks:

At the end our model did not perform as well as I would have hoped. 
We could have done a bit of hyperparameter optimization to further improve our model, but I do not believe it would increase it by a meaningful margin. This is due to the information we got after running a feature importance on the data, it would suggest not a lot of benefit with this dataset.

I used simple models learned at school, and there may be other models that would find more nuanced patterns hiding in the data that would have been more effective to use. Other popular models that involve boosting (LightGBM), would definitely be worth trying.

After we removed the features that we would not know before, it is expeted that the model perform worse. Our new model suggests that there is a very weak connection to our claim amount against the features we kept.

Future adjustments for this project could be to run the model on individual claims which we had dropped at the start. Since we had dropped the property damage feature, it may have been better to only predict the auto insurance claim amount.

Finally, due to the imbalance of claim amounts we may want to use different metric to score the classification or make adjustments to the data accordingly.



