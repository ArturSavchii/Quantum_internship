# Regression on the tabular data
The sape of the dataset is (90000, 53) - 52 features and the target
train.info() shows that we don't have any missing values and object features
From the histograms of every feature we can see that most of them (except 6) have uniform deistribution. Plotting the scatterplot of feature 6 and target we can easily see strong quadratic association.
As our data doesn't have any object features that need to be encoded or missing values and the features are not labeled, so that we cannot construct any new features not knowing their context, we can begin modeling.
Linear Regressin gives us RMSE 29.0154
Decision Tree gives us RMSE 0.0078 -> a huge impovement so we have to try Random Forest which is ensembled model of decision trees
Random Forest with default parameters gives us RMSE 0.0038
Let's use Randomized Search to tune our parameters for RF (decided to use Randomized Search instaed of Grid Search due to its time efficiency)
best_params_ = {'n_estimators': 800, 'min_samples_split': 2, 'min_samples_leaf': 1, 'max_features': 'auto', 'max_depth': 100, 'bootstrap': True}
