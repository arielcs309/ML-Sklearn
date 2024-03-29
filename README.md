# Machine Learning 
Using the package SKlearn

# About the project

The project uses machine learning with the package SKlearn. I tried to predict the house prices.

![Scikitlearn](https://github.com/arielcs309/ML-Sklearn/blob/main/digits-dataset-scikit-learn-machine-learning-python-tutorial-1.png)

## Histogram
``` bash
ax = sns.histplot(data = db1, x= "Price", kde = True)
ax.figure.set_size_inches(20,10)
ax.set_title("Prices Histogram")
ax.set_xlabel('Price');
```
![prices](https://github.com/arielcs309/ML-Sklearn/blob/main/Histogram.png)

## Correlation
Price and square feet have the highest correlation. The others don't have a good correlation since they're close to zero.
![correlation](https://github.com/arielcs309/ML-Sklearn/blob/main/__results___5_0.png)

## Dummies
So I had to create dummies with the code below since there was 3 kinds of neighborhood. 
```bash
db1 = pd.get_dummies(db, columns = ['Neighborhood'],
                    prefix = 'C')
```
![dummy](https://github.com/arielcs309/ML-Sklearn/blob/main/Dummies.png)

## Getting the data ready to train
So I have to split one part of the data to train and the other part to test.
That prevents Overfitting. 
The model shouldn't generalize and if there is new data then it won't be ready to categorize.
I split in 30% test size and 70% train size.
```bash
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.3, random_state=42)
```
# Results
MAE: It's the Mean Absolute Error.  It measures the average of the absolute differences between the predicted values by the model and the actual values of the data. It is less sensitive to outliers. The lower the MAE value, the better the model's performance, indicating that the predictions are closer to the actual values. For example, if the MAE of a housing price prediction model is 1000, it means that, on average, the model's predictions deviate $1000 from the actual housing prices.

MSE: Mean Squared Error. MSE penalizes larger errors more heavily than smaller ones due to the squaring operation. Consequently, MSE tends to be more sensitive to outliers compared to MAE. Lower values of MSE indicate better model performance.

R²:R-squared. R-squared ranges from 0 to 1. Values between 0 and 1 indicate the proportion of variance explained by the model, with higher values indicating better fit.



![results](https://github.com/arielcs309/ML-Sklearn/blob/main/Results.jpg)

# Language
![python](https://github.com/arielcs309/ML-Sklearn/blob/main/python.jpg)

# Author
Ariel Sousa. 
See my [Linkedin](https://www.linkedin.com/in/ariel-candido-22684578/) and my [Kaggle](https://www.kaggle.com/arielsousa)


