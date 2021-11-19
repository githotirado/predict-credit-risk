# predict-credit-risk
Predicting loan credit risk in 2020Q1 dataset by training models using previous year 2019 dataset.  This is lending data from LendingClub.com.

# REFLECTING AND REPORTING (Predicting behavior)
I think the Random Forest classifier will perform better.  Logical Regression is a single predictor model while the Random Forest classifier is an ensemble of decision trees that generally outperforms single predictors.  With a large number of features in the dataset, the Random Forest classifier benefits by considering different combinations of features (with replacement) in its overall prediction.  Conversely, Logical Regression will only use one best fit prediction from the same features.

When scaling data, we are normalizing numeric features with high values to be more proportional to numeric features with lower values to avoid overlooking those features with mainly low values.  I think that with scaling we will get better prediction than with unscaled data, but between Logical Regression and Random Forest classifiers I think we will still see Random Forest classifiers perform better due to lower variance in ensemble methods. 

# Comparison between predicted behavior of the models on unscaled data and the actual results
Logical Regression:
Training Data Score: 0.649671592775041
Testing Data Score: 0.5159506592939175

Random Forest Classifier:(n_estimators = 500)
Training Score: 1.0
Testing Score: 0.6454700127605274

Random Forest Classifier: (n_estimators = 10)
RFC Training Score: 0.9898193760262726
RFC Testing Score: 0.6112292641429179

Initially, the Random Forest Classifier was getting a training score of 100% with testing score around 65% if I used a high number of n_estimators like 500 or 100.  That could mean the model was too complex and was overfitting the training data.  As this is assumed to be a hyperparameter for Random Forest, I reduced the number of n_estimators to 10 trees, and the training score was reduced to 98% with test score of 61%.  So I believe that even though Random Forest Classifier is a complex model, by reducing the number of trees used we could get a better training score and more realistic testing score.  61% testing score for RFC was still better than the 51% for logical regression.  

# Comparison between predicted behavior of the models on scaled data and the actual results
Logical Regression:
Scaled LR Training Data Score: 0.6274220032840723
Scaled LR Testing Data Score: 0.49893662271373884

Random Forest Classifier: (n_estimators = 500)
Scaled RFC Training Score: 1.0
Scaled RFC Testing Score: 0.6448319863887707

Random Forest Classifier: (n_estimators = 10)
Scaled RFC Training Score: 0.9897372742200329
Scaled RFC Testing Score: 0.6099532113994045

Random Forest Classifier: (n_estimators = 3)
Scaled RFC Training Score: 0.9442528735632184
Scaled RFC Testing Score: 0.5935772011909826

Similar to the unscaled comparison, a high number of trees/estimators in the RFC seemed to overfit the training data.  But with fewer trees/estimators, the training score dropped down to 99% (trees=10) or even 94% (trees=3) and produced 59-61% training score which is better than the LR testing score of 50%.