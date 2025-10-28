# Machine Learning Engineer – Practical Coding Test

Duration: 90 minutes  
Dataset: (https://github.com/growexx/public_documents/blob/main/customers.csv)  

## Background

You have recently joined a food delivery startup as a Machine Learning Engineer. One of the challenges the business is facing is customer churn — some users uninstall the application after a few weeks or months of activity. Management wants to build a predictive model that can flag customers who are at risk of uninstalling the app, so that retention campaigns can be launched in advance.

As part of your assessment, you are required to work with a synthetic dataset of 500 customers (customers.csv). The dataset contains the following columns:

*   UserID: Unique identifier for each customer
*   Age: Age of the customer in years
*   Orders: Total number of orders placed by the customer
*   AvgRating: The average rating (out of 5) given by the customer
*   LastLoginDays: The number of days since the customer last logged into the app
*   Uninstalled: The target column, which indicates whether the customer eventually uninstalled the app (Yes or No)

## Task

Your task is to design and implement a complete end-to-end workflow in Python that prepares the data, trains a machine learning model, and evaluates the results. The focus of this exercise is not on using pre-built ML libraries, but on demonstrating your ability to reason about data, implement algorithms, and present results clearly.

1.  **Data Loading and Exploration**  
    Begin by loading the dataset into a Pandas DataFrame. Display the first few rows to understand the structure, and generate basic statistics (mean, median, standard deviation, minimum, and maximum values for numerical columns). This step should help you identify potential issues such as missing values or unusual distributions.
2.  **Data Cleaning and Preprocessing**  
    Check for missing data and explain briefly how you will handle it. Apply an appropriate imputation method (such as replacing missing numerical values with the mean or median). Next, convert the target column Uninstalled into binary form where Yes = 1 and No = 0. Normalize or scale the numeric features so that they are comparable in magnitude before training the model.
3.  **Model Implementation: Logistic Regression from Scratch**  
    **You are required to implement a logistic regression classifier without using any existing machine learning libraries such as scikit-learn.** Write the functions for the sigmoid activation, binary cross-entropy loss, and gradient descent updates. Initialize your model parameters randomly and train the logistic regression model for 1,000 iterations with a learning rate of 0.01. After training, print the final values of the model coefficients.
4.  **Model Evaluation**  
    Once the model is trained, evaluate it on the same dataset. Compute the standard classification metrics including accuracy, precision, recall, and F1-score. In addition, generate the confusion matrix and display the counts for true positives, false positives, true negatives, and false negatives. This will provide insight into how the model behaves across different classes.
5.  **Error Analysis**  
    To demonstrate your understanding of model performance, extract and print at least five rows from the dataset where the model made incorrect predictions. These examples should help illustrate potential weaknesses in the model and areas where data quality or feature engineering might be improved.

## Deliverable

Prepare a Python based complete solution. The script should include both code and explanatory comments where necessary. You are encouraged to use pandas, numpy, and matplotlib for data handling and visualization, but you must not use **pre-built classifiers such as sklearn.linear\_model.LogisticRegression.**