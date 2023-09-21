What Drives the Price of a Used Car?

Problem Statement

Improve the sales of used car by understanding the customer behavior. The data model should help with questions such as,

do customer prefer German or Japanese cars when buying a used car?
do customers prefer black vs grey cars when buying used?
do customers based in certain region willing to spend more on used cars?
What time of the year do customer spend more on buying used cars?

Data Understanding:

We initially read the CSV dataset using Pandas to get an overview of the data.
To gain deeper insights, we generated a Pandas Profiling report, which provided comprehensive details about the dataset's columns.
We also employed Plotly to create histograms, helping us visualize the distribution of various columns within the dataset.

Data Preparation:

In the data preparation phase, we performed the following actions:
    Removed the "VIN," "state," and "region" columns from the dataset.
    Categorized the features into numerical and categorical:
        Numerical Features: "Year" and "Odometer."
        Categorical Features: "Manufacturer," "Model," "Condition," "Cylinders," "Fuel," "Title status," "Transmission," "Drive," "Size," "Type," and "Paint color."
    Utilized different estimators, such as BayesianRidge, DecisionTreeRegressor, ExtraTreesRegressor, and KNeighborsRegressor, coupled with cross_val_score, to determine the best estimator for replacing missing values in the categorical features. BayesianRidge exhibited superior performance.
    Addressed outliers within the "Price," "Odometer," and "Year" numerical features.
    Applied a logarithm transformation to the "Price" target feature to rectify skewness and achieve a more normal distribution.
    Leveraged Plotly and Seaborn to create visualizations post Data Preparation.

Modeling:

Our modeling phase encompassed the following steps:
    Scaled the numerical and target feature columns.
    Segmented the dataset into training (90%) and testing (10%) sets.
    Constructed regression models, including:
        Linear Regression with Recursive Feature Elimination (RFE) and GridSearchCV, yielding an accuracy of 63.231%.
        Ridge Regression with cross-validation and a range of alpha values, achieving an accuracy of 63.244%.
        Lasso Regression with cross-validation and varied alpha values, with an accuracy of 63.008%.
        Random Forest Regression, which outperformed the others with an accuracy of 91.142%.
    Presented a performance table summarizing the accuracy of all the models, with Random Forest Regression emerging as the best-performing model.

Evaluation:

The Random Forest Regression model exhibited the highest accuracy among the models tested.
We created a line graph to visualize and compare the performance of all four models.

Deployment:

A Python function was developed to accept inputs related to car attributes and provide price predictions using the Random Forest Regression model.
The model was deployed on Digital Ocean via a Flask server, enabling users to access a sample API for obtaining used car price predictions.

This comprehensive process allows for efficient price prediction for used cars based on their attributes, benefiting both sellers and buyers.
License

Fabian Schaberl
