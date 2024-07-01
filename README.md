# What drives the price of a car?

<div align="center">
    <img width="800" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/Images/kurt.jpeg">
</div>

![](images/kurt.jpeg)


**OVERVIEW**

In this application, you will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing.  Your goal is to understand what factors make a car more or less expensive.  As a result of your analysis, you should provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.

### CRISP-DM Framework

<div align="center">
    <img width="500" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/Images/crisp.png">
</div>

<center>
    <img src = images/crisp.png width = 50%/>
</center>

To frame the task, throughout our practical applications we will refer back to a standard process in industry for data projects called CRISP-DM.  This process provides a framework for working through a data problem.  Your first step in this application will be to read through a brief overview of CRISP-DM [here](https://mo-pcco.s3.us-east-1.amazonaws.com/BH-PCMLAI/module_11/readings_starter.zip).  After reading the overview, answer the questions below.

### Business Understanding

From a business perspective, we are tasked with identifying key drivers for used car prices.  In the CRISP-DM overview, we are asked to convert this business framing to a data problem definition.  Using a few sentences, reframe the task as a data task with the appropriate technical vocabulary. 

#### Objective: Identify key factors that contribute to the Car Price

The dataset is expected to have gas, hybrid, and electric cars. There are various factors that drive the price of a car. Gasoline cars may have different attributes compared to electric cars. Customer preference also matters. Demand vs. supply also matters.

We have to create an hypothesis about customer preference and validate it against the data.

#### Success Criteria:
For a given set of attributes that exists in the input dataset, our selected model should be able to determine the price of the car with an accuracy of 80%.

Outside the scope of this assignment: The current dataset for this assignment can be divided into two sets: one set that has complete data (all rows have values), another set that has missing data (at least one row has missing value). If we can determine a model that can predict and populate the missing value while maintaining the accuracy of new data, it would be a great model.


#### Situation Analysis:
We have only 1 week to complete the activity. This is the first time we are looking at the data. There are no supporting documentation that provides information about the data except the assignment jupyter notebook.
- Due to the limited time (1 week to complete the activity), we may not be able to perform a detailed exploratory data analysis. 
- We may have to take shortcuts to fix the data quality issues. In some cases, we may have to drop data as it may be too time consuming to fix the quality of the data
- During modeling activities, we may have to fast track some of the work by forcing values to hyperparameters
- Since there is no way to get feedback (from end customers, peer review, or TA), we may end up performing incorrect analysis and spending too much time on wrong section of the dataset
- Some of the attributes may result in multiple values. Performing OneHotEncoder may result in increasing the total number of attributes. Thus expanding our analysis and epocs for model selection & validation
- In the process of cleaning the data, we may mistakenly delete / drop valuable data that be critical to the analysis in the future steps
- We may also cleanse the data too much resulting in synthesized data which does not reflect the true dataset


#### Data Mining Goals and Next Steps:

#### Load and Clean the data:
- Step 1: Load the data into a dataframe and analyze the data for any anomolies
- Step 2: Anomolies can be any one of these:
> - 2a: missing data
> - 2b: outliers (data should be logical; if data does not make sense, exclude them)
> - 2c: If 'year' data is missing, exclude them 
> - 2d: If 'price' data is missing, exclude them. We need to determine what drives the price, without this data, it will be difficult to determine the drivers for 'price'
- Step 3: Create a clean version of the dataset for analysis
- Step 4: Perform Data Quality checks: Completness, Uniqueness, Consistency, and Auditability
- Step 4: Analyze the data for completeness. If data is not required, exclude them
- Step 5: Analyze the data for uniqueness. If the data does not have variety, then we have skewed data
- Step 6: Check for Consistency. Example, electric, hybrid, and gasoline cars have specific attributes. Does the data reflect this
- Step 6: Fill null values; for numeric columns, use mean (average) and for non-numeric columns, use mode (most frequent)

#### Exploratory Data Analysis
- Understand each of the data elements and its patterns
- Identify any correlation between data elements
- Plot the data to visualize patterns

#### Data Prepartion
- Transform the data for modeling
- Split the data into Training and Validation sets

#### Model selection, validation, and tuning
- Apply various models to the dataset
- Validate the model against the hypothesis
- Perform hyperparameter tuning

#### Tools and Techniques + Project Timeline:

#### To perform Exploratory Data Analysis, we will use the following tools and techniques:
- python, pandas, numpy, matplotlib, seaborn, pyplot

#### To perform Data Quality checks, Data Cleaning, we will use the following tools and techniques:
- python, pandas, numpy, sklearn, onehotencoder, matplotlib, pyplot

#### To perform Modeling activities, we will use some or all of the following tools and techniques:
- python, pandas, numpy, sklearn, statmodels, pmdarima, ACF, adfuller, SARIMAX,
- LinearRegression, MAE, MSE, RMSE, K-Means, GridSearchCV, K-Fold, PCA

Project Timeline:
- Due to office workload, I cannot start work on this project until Friday 6/21
- Start the Data Analysis work on Friday 6/21
- Focus on the Business Understanding on Saturday AM 6/22
- Focus on EDA and Data Cleaning activities on Saturday PM 6/22 and Sunday AM 6/22
- Focus on Visualizing the data on Sunday 6/22 PM
- Focus on Data Preparation for Modeling on Sunday 6/22 PM
- Focus on Modeling on Monday 6/23 PM (after office working hours)
- Finalize the materials on Tuesday 6/23 PM (after office working hours)
- Publish the final documents by Tuesday 6/23 PM

Updated Project Timeline:
- Due to office work commitment (production go live weekend of 6/21, some of the work got slipped)
- Request for extension till 7/3 (push hard to get this done before 7/4 )
- Pause work until 6/28 to focus on office post-production issues
- Resume work on 6/28 to finalize Data Preparation, Modeling, and Final summary
- Publish the final document by Sunday 6/30
