# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Housing Price Prediction Through Linear Regression

### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

### Problem Statement 

As a data scientist hired by an investor, I am tasked with determining the relationship between a large set of variables and single family housing prices around Ames, Iowa. This analysis will involve collecting and analyzing data on various factors that may affect housing prices, such as neighborhood, size, and age of the properties. The ultimate goal is to provide the investor with insights on how these factors impact housing prices in the area, and to identify potential opportunities for investment in the single family housing market around Ames, Iowa.

### Executive Summary

This notebook begins by importing two identically formatted datasets from the Kaggle Competition, a test.csv and train.csv to build and test my model.
I structured my data analysis and modeling into four seperate jupyter notebooks:
- Data Cleaning & Exploratory Analysis, where I perform my initial analysis on variables to keep in my model, and create some charts to better conceptualize my data
- Transformations & Training, where I make appropriate normalizing transformations on my data. 
- Test Data Organization, where I make the same transformations on my testing data to keep consistant.
- Model Analysis, where I fit the models that I have built to the test data, and format my predictions to be submitted online.

Through creating a few models to predict housing prices, I was able to better understand the variables that drive value in the single family housing market of Ames Iowa.

### Data Dictionary
Provided by the Competition: https://www.kaggle.com/competitions/1031-ames-competition/data

### Conclusions and Recommendations

After carefully examining the training dataset, I went through each variable in the test data to evaluate which ones would be most worth keeping in the regression model. I made a few initial cuts just due to the fact that, for example, most of the data had a garage, and very few had a pool. 

I made decisions on data imputation based on the variable types and the distribution of each variable to evaluate the potential impact of imputation on the model's accuracy. For example, for numeric variables, I used the mean value to impute missing data if my dataset was fairly unskewed, whereas I used median if there were any outliers in the dataset. In contrast, for categorical nominal variables, I used the mode values for imputation. In the ordinal case, there were datapoints where null values actually indicated that a particular field did not apply to a home. In this case, I would impute 0 (as part of my broader custom ordinal data transformations).

The next step was data tranformation and normalization, which occured differently across the dataset.
- Nominal Data: I performed one-hot encoding to create dummy variables for each nominal category
- Ordinal Data: In the most time-consuming aspect of my project, I built custom dictionaries to map ordinal values to a value 1 through n, such that n is the number of ordered values in a category
- Numerical Data: I normalized the data with z-scores to show where datapoints fell into their distributions within the data.

After applying the above transformations to both the testing and training data, the final step of this project was the modeling portion. I first built a very-overfit purely linear model, whose overfitting was evidenced by a 71-thousand RSME score in kaggle. To determine which variables were most closely related to my model, I built both a lasso and ridge model to apply constraints to the value of the coefficients. The lasso allowed me go from 201 variables to 83, which was very effective in reducing the overfitting in my model. Using those 83 verified variables, I ran another linear regression, which brought me to an approximate 90% R2, and ~27000 RSME on my training data. 

Ultimately there are a few ways I could improve my project going forward:
- Look into polynomial variables; though I didn't utilize this, I would be very interested to see how the variables react
- Program with object oriented design to optimize code reusability
- Start smaller and grow the project from there: If I had spent more time focusing on the core variables, rather than spending considerable time on the transformations of less important variables, my model could have been more effective.

CONCLUSION 1: *Housing Predcition Levers appear to change as home values roughly exceed $300,000-400,000*
Though there could be some multicollinearity in my model that remains to be removed in my model, there is certainly an extent to which it appears that home pricing changes in nature in this town as housing prices exceed 300 thousand dollars. As shown in my histogram and box & whisker plot of the distribution of the target in my data cleaning notebook, there is a right skew in the data, with plenty of outliers. There is certainly curioscity of how my valuation model could have improved if I created two models, one to handle high-value homes in Ames vs. those falling within the center of the distribution. 

CONCLUSION 2: *Lasting quality features drive value.* Ultimately, the lasting, difficult to change aspects of the real estate is what drives values. The location, the external quality, the municipal zoning, these difficult to change element instill value in the real estate

Suggestions from my Research:
- My model appears strongly effective up until approximately $350 thousand.  

- Intrinsic value is often driven by difficult to change features of real estate.

SOURCES:
- Kaggle Dataset


[data]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/Data
[deliverables]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/Deliverables
[rubric]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/Rubric
[presentation]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/Presentation
[ps]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/Problem-Statement
[background]: https://git.generalassemb.ly/dsir-1031/project_1/wiki/SAT-ACT-background
