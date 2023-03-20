# Regression on the tabular data
### Data Analysis
<p>The shape of the dataset is (90000, 53) - **52 features and the target**<br>
train.info() shows that we don't have any missing values and object features<br>
From the histograms of every feature, we can see that most of them (except 6) have a **uniform distribution**. Plotting the scatterplot of feature 6 and the target, we can easily see **a strong quadratic association**.<br>
As our data doesn't have any object features that need to be encoded or missing values and the features are not labeled, we cannot construct any new features not knowing their context, and we can begin modeling.<br></p>
### The Model
<p>**Linear Regression** gives us **RMSE 29.0154**<br>
**Decision Tree gives** us **RMSE 0.0078** -> a huge improvement, so we have to try Random Forest, which is the ensembled model of decision trees<br>
**Random Forest** with default parameters gives us **RMSE 0.0038**<br>
Let's use **Randomized Search** to tune our parameters for RF (decided to use Randomized Search instead of Grid Search due to its time efficiency). For randomized search we will use a **random sample** of 500 observation, as it will take to to much time<br>
'''best_params_ = {'n_estimators': 800, 'min_samples_split': 2, 'min_samples_leaf': 1, 'max_features': 'auto', 'max_depth': 100, 'bootstrap': True}'''<br>
**RMSE = 0.00365** - Our predictions are very close - in 100% of observations, we correctly predict the integer part of a target.<br>
I noticed that the decimal part equals to '7' feature.<br>
![image](https://user-images.githubusercontent.com/68689076/226411296-dd59d9f1-a018-49c5-abf2-fee4c80ba53e.png)
Thus, as our integer part is always correct, for every predicted target, we can replace a decimal part with the '7' corresponding feature. - **RMSE = 3.05*10<sup>-15</sup>**.<br>
(The last step was a little tricky, but even without it, the model gives good predictions)<br>
