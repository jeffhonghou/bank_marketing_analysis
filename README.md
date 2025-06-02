# Report of the bank marketing analysis

## Link to the Jupyter notebook
[My Jupyter notebook](https://github.com/jeffhonghou/bank_marketing_analysis/blob/main/prompt_III.ipynb)

### Problem 1: Understanding the Data
To gain a better understanding of the data, please read the information provided in the UCI link above, and examine the **Materials and Methods** section of the paper.  How many marketing campaigns does this data represent?
#### Step 1.1: How many marketing campaigns does this data represent?
This data represents 17 marketing campaigns.

### Problem 2: Read in the Data
Use pandas to read in the dataset `bank-additional-full.csv` and assign to a meaningful variable name.

### Problem 3: Understanding the Features
Examine the data description below, and determine if any of the features are missing values or need to be coerced to a different data type.
#### Step 3.1: determine if any of the features are missing values
Any feature bearing positive values returned from df.isna().sum() has missing values.
#### Step 3.2: determine if any of the features need to be coerced to a different data type
Any feature bearing NaN values in the mean field return from df.describe(include='all') will need to be coerced to a different data type.

### Problem 4: Understanding the Task
After examining the description and data, your goal now is to clearly state the *Business Objective* of the task.  State the objective below.
#### Step 4.1: Business Objective
Determine which client attributes and marketing features most influence whether a client subscribes to a term deposit, in order to optimize future marketing campaign strategies for improved effectiveness and targeting.

### Problem 5: Engineering Features
Now that you understand your business objective, we will build a basic model to get started.  Before we can do this, we must work to encode the data.  Using just the bank information features, prepare the features and target column for modeling with appropriate encoding and transformations.
#### Step 5.1: Encoding
Performs one-hot encoding to categorical features.
#### Step 5.2: Scaling
Performs scaling to numerical features.

### Problem 6: Train/Test Split
With your data prepared, split it into a train and test set.

### Problem 7: A Baseline Model
Before we build our first model, we want to establish a baseline.  What is the baseline performance that our classifier should aim to beat?
#### Step 7.1: What is the baseline performance that our classifier should aim to beat?
Our classifier should aim to achieve significantly better performance than this baseline, particularly in terms of precision, recall, and F1-score for the positive class (y = yes/1), which represents the key outcome of interest.

### Problem 8: A Simple Model
Use Logistic Regression to build a basic model on your data. 

### Problem 9: Score the Model
What is the accuracy of your model?
#### 9.1 The accuracy of my model is 0.9110220927409566.

### Problem 10: Model Comparisons
Now, we aim to compare the performance of the Logistic Regression model to our KNN algorithm, Decision Tree, and SVM models.  Using the default settings for each of the models, fit and score each.  Also, be sure to compare the fit time of each of the models.  Present your findings in a `DataFrame` similar to that below:

| Model | Train Time | Train Accuracy | Test Accuracy |
| ----- | ---------- | -------------  | -----------   |
|     |    |.     |.     |


| Model                    | Train Time | Train Accuracy | Test Accuracy |
|--------------------------|------------|----------------|----------------|
| Logistic Regression model | 0.201142   | 0.911927       | 0.911022       |
| KNN algorithm             | 0.002884   | 0.928619       | 0.903010       |
| Decision Tree             | 0.426489   | 1.000000       | 0.886380       |
| SVM models                | 29.861710  | 0.856722       | 0.845472       |

### Problem 11: Improving the Model
Now that we have some basic models on the board, we want to try to improve these.  Below, we list a few things to explore in this pursuit.
- More feature engineering and exploration.  For example, should we keep the gender feature?  Why or why not?
- Hyperparameter tuning and grid search.  All of our models have additional hyperparameters to tune and explore.  For example the number of neighbors in KNN or the maximum depth of a Decision Tree.  
- Adjust your performance metric
#### Step 11.1: Reloading dataset and apply more feature engineering and exploration - categorical features
#### Step 11.2: More feature engineering and exploration - numerical features
#### Step 11.3: Applying encoding and scaling
#### Step 11.4: Hyperparameter tuning and grid search
Using GridSearchCV to find best parameters for each model
#### Step 11.5: Adjust your performance metric
Adjust the performance metric for each model based on the GridSearchCV results from step 11.4

| Model                    | Train Time | Train Accuracy | Test Accuracy |
|--------------------------|------------|----------------|----------------|
| Logistic Regression model | 0.177844   | 0.911168       | 0.912115       |
| KNN algorithm             | 0.005552   | 0.921335       | 0.908352       |
| Decision Tree             | 0.080536   | 0.917329       | 0.915149       |
| SVM models                | 16.340876  | 0.917451       | 0.909444       |
#### Step 11.6: Print the coefficients of Logistic Regression
| Feature                        | Coefficient  |
|--------------------------------|--------------|
| month_mar                      | 1.908114     |
| duration                       | 1.208996     |
| euribor3m                      | 1.146090     |
| cons.price.idx                 | 1.042454     |
| poutcome_success               | 0.860618     |
| month_aug                      | 0.857969     |
| poutcome_nonexistent           | 0.411524     |
| job_retired                    | 0.238156     |
| month_sep                      | 0.233414     |
| education_illiterate           | 0.232788     |
| job_student                    | 0.165145     |
| month_oct                      | 0.151400     |
| education_university.degree    | 0.142633     |
| month_jul                      | 0.131970     |
| education_basic.6y            | 0.097044     |
| job_unemployed                 | 0.073793     |
| job_technician                 | 0.062629     |
| month_dec                      | 0.046754     |
| marital_single                 | 0.025181     |
| education_unknown              | 0.006440     |
| default_yes                    | -0.012886    |
| education_professional.course  | -0.014774    |
| education_high.school          | -0.026164    |
| previous                       | -0.027446    |
| marital_married                | -0.028211    |
| education_basic.9y            | -0.034149    |
| job_management                 | -0.052300    |
| job_housemaid                  | -0.075455    |
| marital_unknown                | -0.080225    |
| nr.employed                    | -0.081497    |
| job_services                   | -0.116146    |
| job_entrepreneur               | -0.130887    |
| pdays                          | -0.196642    |
| job_blue-collar                | -0.200379    |
| job_unknown                    | -0.273490    |
| default_unknown                | -0.283657    |
| job_self-employed              | -0.301383    |
| month_jun                      | -0.396870    |
| month_may                      | -0.524042    |
| month_nov                      | -0.565595    |
| contact_telephone              | -0.633846    |
| emp.var.rate                   | -2.718989    |

## Findings
### Comparison results
The Decision Tree model offers the best performance in terms of test accuracy, while Logistic Regression strikes a good balance between speed and performance. KNN is suitable for extremely fast training needs, though it slightly underperforms on test accuracy. SVM may be less practical due to its high computational cost without a significant accuracy advantage.
### Next steps and recommendations
March is the most effective month for running the bank marketing campaign, followed by August. In addition to timing, the top five features that most influence clients' acceptance of term deposits are: the duration of the last contact, the daily Euribor 3-month rate, the monthly consumer price index, and the outcome of the previous campaign—particularly if it was successful, and the employment variation rate - quarterly indicator. Therefore, future campaigns should strategically prioritize these factors to enhance overall efficiency.