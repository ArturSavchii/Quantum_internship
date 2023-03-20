# Regression on the tabular data
<p>The sape of the dataset is (90000, 53) - 52 features and the target<br>
train.info() shows that we don't have any missing values and object features<br>
From the histograms of every feature we can see that most of them (except 6) have uniform deistribution. Plotting the scatterplot of feature 6 and target we can easily see strong quadratic association.<br>
As our data doesn't have any object features that need to be encoded or missing values and the features are not labeled, so that we cannot construct any new features not knowing their context, we can begin modeling.<br>
Linear Regressin gives us RMSE 29.0154<br>
Decision Tree gives us RMSE 0.0078 -> a huge impovement so we have to try Random Forest which is ensembled model of decision trees<br>
Random Forest with default parameters gives us RMSE 0.0038<br>
Let's use Randomized Search to tune our parameters for RF (decided to use Randomized Search instaed of Grid Search due to its time efficiency)<br>
best_params_ = {'n_estimators': 800, 'min_samples_split': 2, 'min_samples_leaf': 1, 'max_features': 'auto', 'max_depth': 100, 'bootstrap': True}<br>
RMSE = 0.00365 - Our predictions are very close - in 100% of observations we correctly predict the integer part of a target. I noticed that the decimal part equals to '7' feature.<br>
![image](https://user-images.githubusercontent.com/68689076/226411296-dd59d9f1-a018-49c5-abf2-fee4c80ba53e.png)<br>
Thus, as our integer part is always correct, for every predicted target we can replace decimal part with the '7' corresponding feature. - RMSE = 3.05 * 10^-15.<br>
(The last step was a little tricky, but even without it the model gives good predictions)<br>
