# Google-Revenue-Prediction
Kaggle Competition - Top 5 solution  in Leader board

## Project Definition & Introduction
Google Store (Gstore) is an online hardware retailer operated by Google. Lots
of people visit Google Store every day, which generates h11uge volumes of
data. Using Google analytics, each transaction in GStore has been tracked and
reported, including website traffic, transaction data, customer buying behavior
and customer demographics. This data can be valuable when Google analyzes
their customer base and design marketing strategies.
In this project, we use the Google Store dataset to predict revenue per
customer. This outcome is useful not only for Google but also for companies
who want to make use of Google Analytics to assist data analysis, informing
them with actionable promotional efforts and marketing investments.

## Solution Overview
Firstly, we want to know whether a customer will return to the store in the
next 2 months. So we build a classification model to predict whether a
customer will come back or not. If the customer returns in the next two
months, we mark it as the return group. Otherwise, we mark it as the nonreturn
group. In this step, we build three models, including random forest,
XGBoost and LightGBM. We use accuracy to evaluate random forest and
XGBoost model and binary cross-entropy to evaluate LightGBM model. After
identifying the return group customers, we are interested in how much they
will spend. Then we build another regression model to predict how much one
customer will spend in the Google Store. In this process, we build three
models, including random forest, XGBoost and LightGBM. We use RMSE to
evaluate our models.

## Analysis

The problem in hand was to predict the future two months revenue of
customers using their 5 months historical purchase data. Hence, the first
major step in our analysis was to make training data simulate the problem we
are trying to solve as it involves predicting customer revenues for the future
two months after 42 days of gap between available data. As we didn’t have any
information about the lagged time of 42 days; we prepared our data to follow
the same pattern by adding two columns using available dataset; one whether
the customer will return to the site or not after the lagged time and if returned
what would be their average spend.
Once we had the strategy set, the next step was to clean the data so that to get
much of the information out from the JSON columns, removing variables
which are not adding to any information gain and encoding categorical
variables to be used in models. Next step was to select algorithms to test our
predictions on. Also, since we have to predict both the return label and
revenue, we built two models; one for classification and other for revenue
prediction. We choose tree-based models as they use bagging and boosting
techniques to improve predictions and are more efficient as they work on a
subset of data for building each tree. We tried three models viz. Random
Forest, XG Boost and Light GBM on the train set with 30 variables and checked
for the feature important variables to further subset our features. This helped
us improve both the prediction accuracy/RMSE and computation time.
Next for model evaluation, we just multiplied our classification output (which
is whether a customer will return) with the regression output (which predicts
the expected revenue value). After checking for the RMSE value for the three
models we have built, Light GBM gave us the best RMSE of 0.88188.

![Google_Table](https://user-images.githubusercontent.com/25751360/80908365-ea539600-8ce4-11ea-8c83-7e8081259891.JPG)

