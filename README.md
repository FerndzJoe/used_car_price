# What drives the price of a car?

<div align="center">
    <img width="800" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/kurt.jpeg">
</div>

**OVERVIEW**

In this application, you will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing.  Your goal is to understand what factors make a car more or less expensive.  As a result of your analysis, you should provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.

### CRISP-DM Framework

<div align="center">
    <img width="500" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/crisp.png">
</div>

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

### Observations:

##### Data Issues:

- The original observed dataset had 426,880 records. Many of the attributes had incomplete data resulting in poor data quality
- Excluding many of the data and normalizing the remaining, we ended up with only 102,680 records.
- We had a lost off 324,200 records due to poor quality data. Due to limited time, further research was not possible on the missing dataset
- To perform high quality prediction and to develop a model, a good population of the data is required

##### Encoding Issues:
- Ordinal and One Hot Encoding had limited effect of the data due to large portion of missing data.
- Some of the ordinal values had good data while others did not. Some of the One Hot Encoded values had poor data
- Results reflected strong contributors to predictions when values existed and there were variance in the data to build correlation

#### Ordinal Encoding 
**condition :** Ordinal will be : salvage, fair, good, excellent, like new, new

**cylinders :** Ordinal will be : 3 cylinders, 4 cylinders, 5 cylinders, 6 cylinders, 8 cylinders, 10 cylinders, 12 cylinders, other

**title_status :** Ordinal will be : salvage, parts only, missing, rebuilt, lien, clean

**drive :** Ordinal will be : rwd, fwd, 4wd

**size :** Ordinal will be : compact, sub-compact, mid-size, full-size

#### One Hot Encoding (OHE)

**type :** Values for OHE will be : 'hatchback', 'coupe', 'sedan', 'convertible', 'SUV', 'wagon', 'pickup', 'other'
 'van' 'truck' 'mini-van' 'offroad'

**paint_color :** Values for OHE will be : 'white', 'red', 'silver', 'black', 'blue', 'grey', 'green', 'brown', 'yellow',
 'orange', 'custom', 'purple'

**transmission :** Ordinal will be : manual, automatic, other

**fuel :** Ordinal will be : gas, diesel, hybrid, electric, other 

Using Linear Regression, and GridSearchCV, cleaned dataset resulted in:

- Ridge simple cross validation Train MSE: 92493878.08389969
- Ridge simple cross validation Test MSE: 93180363.61416017
- Best Ridge Alpha: {'ridge__alpha': 68.66488450043002}

Using K-Fold of 10, cleaned dataset resulted in:
- Ridge k-fold cross validation Train MSE: 92498992.3769556
- Ridge k-fold cross validation Test MSE: 93134068.70667933
- Best Ridge Alpha: {'ridge__alpha': 1.0}

Performing the Permutation Importance on the cleaned dataset resulted in:
- The model score value is:  -110072110.262
- The Permutation Importance for all the wage dataset are:

```
remainder__year          48,085,875.612 +/- 916142.548`
remainder__odometer      33,244,440.367 +/- 662899.713`
cat__fuel_diesel         12,059,939.628 +/- 251941.997
cat__type_pickup         9,882,418.760 +/- 414450.272
cat__type_sedan          6,038,728.832 +/- 390215.323
cat__type_truck          4,909,030.036 +/- 258168.142
ord__cylinders           2,985,739.807 +/- 231146.927
cat__type_hatchback      2,860,376.142 +/- 227691.510
cat__fuel_gas            2,728,432.247 +/- 155349.256
ord__drive               2,052,602.233 +/- 181385.830
ord__title_status        1,063,371.860 +/- 99859.356
cat__type_wagon            899,228.642 +/- 122959.810
cat__type_SUV              766,152.454 +/- 157775.801
cat__type_mini-van         331,500.759 +/- 73574.842
cat__paint_color_black     300,529.166 +/- 107741.581
cat__type_convertible      233,274.952 +/- 108409.081
cat__paint_color_silver    144,333.551 +/- 26627.525
cat__fuel_hybrid           137,912.917 +/- 46731.006
cat__paint_color_grey       62,346.088 +/- 18552.870
cat__paint_color_blue       49,842.279 +/- 17584.877
cat__paint_color_yellow     39,509.918 +/- 17839.834
cat__paint_color_green      25,361.510 +/- 9366.497
```

#### Visualizations from the analysis

<div align="center">
    <img width="800" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/corr_heatmat.png">
    <img width="700" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/distrodometer.png">
    <img width="700" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/distrprice.png">
    <img width="700" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/distryear.png">
</div>

#### Learning Curve Results:

<div align="center">
    <img width="500" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/k-fold-lcurve.jpeg">
    <img width="500" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/k-fold-ridge.jpeg">
</div>

#### Actuals vs Predicted Values:

<div align="center">
    <img width="600" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/ActualvsPredicted1.jpeg">
    <img width="600" alt="image" src="https://github.com/FerndzJoe/used_car_price/blob/main/images/ActualvsPredicted2.jpeg">
</div>


### Conclusion

This project used the structured CRISP-DM framework to address the business problem. All missing data was either removed or resolved by leveraging data from other attributes / records. With the limited data, the following observations were made.

|Attribute|Impact|Observation| Recommendation|
|:-----------|:----------:|:-------------------------------------------------------|:-------------------------------------------------------|
|Id|None|Not critical and was ignored for the analysis|Good to use as index reference|
|Region|Low|Not a major contributor for the analysis at macro level|Can be used to breakup data by region and analyze for targeted results|
|Year|High|Important attribute as it is directly correlated to the price of the car. The older the car, the cheaper it gets. However, if the car is very old and in good condition, the price increases or remains stable|Rank the car price by year and compare over the past years to see how the price of car performs over the years. This will give a good indication on which cars to focus and secure for resale|
|Manufacturer|Unknown | There are 41 unique manufacturers. Some of them have less than 10 cars and does not provide enough insight to make a recommendation. Also some of the manufacturers listed are actually models of vehicles (ex: ram, gmc) resulting in bad data. The top 10 manufacturers contribute to 68% of the data |Analyzing the top 10 manufacturers may provide good insight into resale. This may be more productive and time saving than analyzing all the data (use 80-20 rule)|
|Model|Unknown |There are 15,425 unique models in the cleansed dataset (29,649 unique models in original dataset). Top 10 models contribute to only 11% of the data. Top 1,000 models contribute to 50% of the data. Since this data is free text, it was not considered for the analysis.|Focus on converting the model data to numeric value in comparison with manufacturer, transmission, cylinder, and other dependent attributes (use general knowledge to perform the comparison). Numeric value can be used in the model to determine the correlation and influence on the car price. Also identify similarities between models and create subgroups based on data from other attributes like manufacturer, cylinder, fuel, transmission, size, and type. Convert this to numeric value for further analysis|
|Condition|High |More than 50% of the data are nulls and unusable unless further analysis can be done to replace the missing data. The value of price is directly correlated to the quality or condition of the car.|Find ways to improve the quality of the data either through better data acquisition techniques or using exploratory data analysis (EDA) to fill missing values. Comparing the missing data against others that have values can provide better insight to update the missing data. Also, analyze price impact based on specific values of condition.|
|Cylinders|Medium |Approximately 42% of the data are nulls and unusable unless further analysis can be done to replace the missing data. Price range depends on the cylinders. However, some prices were poorly represented and impacted the price range to analyze data using cylinders. The 12 and 8 cylinder vehicles have higher price while 3 and 5 cylinders result in less price. Also, the data shows that there are 27 manufacturers that make 5 cylinder cars. However, there are less than 10 manufacturers that make 5 cylinder cars. So cleaning up the data is critical to get accurate results |Invest time to clean up the data and find ways to separate data by cylinder and analyze for better accuracy of the resale car price. Incorrect data like 5 cylinders have to be addressed or excluded before further analysis can be done. It can badly influence the results and recommendations|
|Fuel        |High |Based on the analysis, diesel cars seem to generate the highest price. However, in reality we know that the production and sales of diesel cars are declining due to environmental issues. There are only 7% of the data that represent diesel cars.|Detailed analysis has to be performed to see why diesel cars have such high correlation. Alternatively, excluding diesel cars (knowing that many states are banning sale of diesel car) may be beneficial as the recommendation may not be useful information for car resale|
|Odometer    |High |New, like new, and good cars have higher resale price. Cars with excellent rating are not resulting in higher resale. The contributing factor to the condition is the odometer reading. A car with lower miles and better condition results in higher resale price. Higher miles on the car reduces the bargaining powerfor the car dealer|Focus on acquiring used cars that have low mileage. Customers prefer to buy newer cars compared to cars in excellent condition.|
|Title_status|Low|While the title status is not critical for car resale, a missing title impacts the resale price. Customers tend to prefer lien and clean car title|Focus on acquiring cars that have clean title. Reducing spending time on cars that are salvaged, parts only, or missing title. It may cost more for the dealer to sell these cars compared to a lien and clean title cars.|
|Transmission|Unknown|There are only 3 types of transmissions in the dataset. The automatic transmission has higher number of records while other category resulted in higher sale price. Based on data, it would be best to focus on automatic transmission. The manual cars were fewer and provided the least resale price |Focus on acquiring automatic transmission cars and use other attributes to determine resale price|
|VIN|Low|The VIN number does not have any impact to the resale of a car unless the VIN number is very low and someone is really looking for a specific VIN number. Ignoring this data can save time in the analysis. However, before you ignore the data, you can use this data to compare if there is any missing data and replace them.|Use VIN information to find missing data and use the record with the most information.|
|Drive|Low|30% of the original dataset was missing data. There are 3 types of data in the dataset - 4 wheel drive (4WD), forward wheel drive (FWD), and rear wheel drive (RWD). Data indicates we have higher number of 4WD vehicles for sale. There are very few FWD vehicles. More customers choose 4WD compared to other cars.|Focus on acquiring 4WD cars and highlight its benefits to potential buyers. While FWD and RWD are fewer in numbers, futher analysis needs to be performed by region to determine if FWD or RWD has a higher chance of resale in a specific location.|
|Size|Unknown|72% of the original dataset was missing data. There are only 4 sizes namely, full, mid, sub-compact, and compact. However, there are higher number of full size cars indicating higher sale volume and availability for resale.|Size plays a big role in the resale price. Bigger vehicles with the right cylinders, condition, and mileage can result in higher resale price. With limited data available, the correlation was not enough. Focus on acquiring cleaner data that helps improve the quality of this attribute.|
|Type|High|Trucks, Pickups, and SUVs have higher counts in the dataset. Only 22% of dataset is missing values.|Focus on acuqiring SUVs, Pickups, Trucks, and Vans. These tend to sell faster than regular sedansm coupe, and convertables. Understanding the customer base and region specific would be more critical. Further analysis by state and region can help drive better decision for acquisition and resale of cars.|
|Paint_color |Low|31% of the data was missing color information. Yellow and black seem to be the available data. A particular car color did not have a major impact on the price of the car|Understand the customer segment and perform more indepth analysis by car paint color to determine if this is relevant. Then secure cars for resale for colors that customers prefer.|
|State       |Low     |There are 51 unique states represtend in this dataset. Top 10 states contribute to 50% of the data. There were no missing data in the state attribute |Analyzing the dataset for top 10 states would provide good insight and save time analyzing the full dataset. Additionally, analyzing data by state and then by region would provide more customized resale value than comparing it across all 50 states. Demand for certain types of cars may be state/region specific and would provide critical and valuable information for car resellers|
|Price       |Target  |Inconsistency in the data and high subset of anomolies prevented from using all the data. Reviewing data by sampling, it was observed some of them were incorrect. Price of car was set to 1, 2, 3... 10 and may not truly reflect the actual price    |It would be best to invest time to secure cleaner data. Further research could help remove bad data or correct them based on other attributes|

#### Approach and Future work

Having completed the analysis and summarized the finding, here are some of my recommendation in case someone is planning to redo this exercise.

- Perform 4 different sets of analysis
  1. Remove all missing values and process only records that have all the values in each row
  2. Separate the data by state and region; analyze them separately. The resale price of a car in one state will be different from others as the customer preferences vary
  3. Before removing all the missing values, use other attributes to determine if missing data can be recreated. For example, an electric car does not have cylinders. It should remain null and should be acceptable. Replace null with 'not applicable'. That way we are not removing null rows. Similarly, find anomolies and exclude them. For example, there are fewer manufacturers that make and sell 5 cylinder cars. Also, based on regulatory needs, some dataset can be eliminated such as cars with fuel type diesel. Focus on gas, electric, and hybrid for analysis
  4. Remove columns that are not required for analysis and consolidate columns if possible. For example, State and Region can be analyzed and only one of them may be required for analysis
 
- Based on data visualization, further reduction of data can be made such as excluding anomolies. Also in some cases, applying Ordinal or Label encoding may be better than One Hot Encoding. Use different approaches to determine how the data is correlated

- Perform VIF and Permutation Importance before we start modeling. It will help us reduce the number of attributes and also help identify multicollinearity.
  
- Once we have a clean dataset, apply modeling and prediction.

#### Insights and Next Steps

- **Acquisition of Cars for resale:** Focus on acquiring newer cars or like newer cars. If the cars are used for a longer period of time, focus on lien or clean title cars. Additionally, focus on aquiring trucks, pickups, suvs and minivans. Do not acquire convertables and offroads as data indicates the sale is fewer in number. Do not acquire diesel cars as the regulations indicate customers will switch to electric, hybrid, and gasoline cars.
  
- **Improve Car Sales data:** Focus on acquiring cleaner dataset or invest money in cleaning up existing data. Research has to be done to understand the relationship between each attribute and use that to clean the data. Poor dataset will not yeild in good recommendation. Some of the price for cars were 1 through 20. This does not look like clean data and must be improved. On the other extreme, some of the cars showed sale price of 5 million or more. Acquire car sales data for electric, hybrid, and gasoline cars and for trucks, pickups, suvs, and minivans.
  
- **Pricing Strategy:** Analyze the data and create pricing strategy by State and Region. The sale price of a used car varies by state and region. Knowing the customer and the economic condition is critical to determine which car would be best for the customer. Additionally, acquire DMV data for cars and economic data. Use both this data to improve the pricing stategy for used car resale price.

- **Continuous Model Refinement:** As we cleanse and acquire new data, it is important to revisit the model and refine them. Capture actual results of car resale price and compare them with existing data. If the data does not match the predicted values, models need to be refined further. Once we are able to predict the resale price of a car, it may reset the baseline of the existing data and trigger a need to rework the models for new baseline. It is important to understand that and continuously refine the models. 

## Repository Structure
- <code>notebook/used-car-price-prediction.jpynb</code>: Jupyter notebook with code.
- <code>README.md</code>: Summary of findings and link to notebook

## Notebook
The detailed analysis and code can be found in the Jupyter notebook <a href="https://github.com/mitbans/used-car-price-prediction/blob/main/notebooks/used-car-price-prediction.ipynb">here</a>.
