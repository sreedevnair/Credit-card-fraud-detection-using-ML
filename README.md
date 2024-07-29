# Credit Card Detection using Basic ML

In this project, we will predict whether a credit card transaction is valid or not. 

It's a binary classification problem and we will be using a Logistic Regression model to predict whether the transaction is legit or not.

## Notes :-

### 1. `.isnull()` Function
This is function will return the complete DataFrame with `True` or `False` values. If the value is not present (i.e. a Null value), it will show `True`, otherwise `False`.

To check the total number of Null values present in the DataFrame, we use `.isnull().sum()`. This will return Series with the number of Null values in each column (feature).

### 2. `.dropna()` Function
This function will return a new DataFrame with all the rows removed that contains one or more *Null* values.

We use `inplace=True` parameter to save the changes in our original DataFrame.

It also have another parameter `axis` which is set to 0 by default. When set `axis=0`, the operations will be done row wise and if `axis=1`, the operations will be done column wise.

### 3. `value_counts()` Function
We use this function to check the occurences of unique values of a particular column. In our case, we are trying to check the number of legit transactions (where *Class* equal to 0) and number of fraudulent transaction (represented by *Class* equal to 1).

### 4. Unbalanced DataSet
This is a highly unbalanced data set as we have a lot of legit transactions and only few fraudulent transactions. In this case, the ML model won't be able to find patterns between the features of fraudulent data.

### 5. `.groupby()` Function
This function is used to group the Dataset based on the possible values of the column name that we mention as the paraemeter. Then we would have to mention the operation that we would to perform on the grouped data.

### 6. Under sampling
To balance this data set, we will use a technique called Under Sampling.

**Undersampling** is a technique to balance uneven datasets by keeping all of the data in the minority class (which is the fraudulent transaction in our case) and decreasing the size of the majority class (legit transaction).

To do this, we will randomly fetch the data from legit transaction that is of the same size as of fruadulent data. Once we have the data set with equal sizes, we will simply merge them.

### 7. `.sample(n = Number_of_rows)` Function
This function is used to randomly select number of rows from a dataset.

### 8. `.pd.concat()`
We use this function to merge to DataFrames. We have to pass the list of DataFrames that we want to merge and then the axis (same logic as mentioned in `.dropna()`)

### 9. Creating the Feature DataFrame and Target Series
To do this, we are simply dropping the *Class* (since that's our Target) column from the dataset  to get the Feature DF and just selecting the *Class* column for our Target Series.

### 10. Splitting the data
Before we train the model, we need to split the data into 2 sets :-
1. Training set
2. Test or validating set.

To split the data, we are using the function `train_test_split()`.

We are passing 4 parameters in this function :-
1. The feature dataset
2. The target dataset
3. `test_size` : By default it's .25, which means 25% of the dataset will be used for testing and the other 75% for the training.
4. `random_state` : This is to make sure that our data split remains same during every execution.
5. `stratiify` : It basically ensures that the data split have the same proportions every time.

### 11. Training the model
Here, we are creating a model of `LogisticRegression()` class.

We train, predict, and score the model in the same way we train Decision Tree model or Random Forest model.

<br><br>

> This project was a complete walkthrough of this [tutorial](https://youtu.be/NCgjcHLFNDg?si=hQSOsp_KZ4r1Owsv) by Siddhardhan.
