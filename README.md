# Phase 2 Project

![king_county_.jpg](https://github.com/jordanate/phase-2-project/blob/main/images/king_county_.jpg)

**By**: Jordana Tepper

## Overview

This project analyzes existing data about house sales in King County, Washington, from 2014 - 2015 in order to develop a predictive model that can aid a stakeholder in determining what zip code they should buy a house in based on their budget and criteria for their new home. The dataset used in this project includes information about various aspects of a home, such as the number of bedrooms, zip code, and square footage. After utilizing the process of exploratory data analysis, I create multiple linear regression models to eventually reach the model with the lowest error. Finally, I provide three zip codes for the stakeholder that best fit their preferences for their home, along with the respective predicted prices.

## Business Problem

An elderly couple, Bruce and Carol, are from King County, Washington, and want to downsize from their current home as there is no need for them to deal with the maintenance of a large house anymore. Nevertheless, in the past few years, Bruce and Carol have become grandparents and want a home with enough room for their two grandchildren to sleep over and play outside. Bruce and Carol have a set criteria for what they want in a house but do not know where in King County they should look to fulfill such preferences.

Therefore, the goal of this project is to build a predictive model based on real data from house sales in King County, Washington that can answer the following question: **In which zip code should the stakeholders purchase their home based on the criteria listed?**

## Data

The data that I use for my projects comes from a dataset from Kaggle about King County, Washington House Sales in 2014-2015. This source includes information such as square footage, number of bedrooms, number of bathrooms, zip code, number of floors, condition of the house, and quality of the view.

## Modeling

After doing some data cleaning, I perform a 70%-30% Train-Test Split on the data with price as the target variable and all other variables as the predictors. Next, I create multiple linear regression models. 

The process that I use to reach my final model involve the following steps:
* Making categorical columns more interpretable (ex: date, zip code, condition) through One Hot Encoding and Ordinal Encoding
* Standard Scaling my predictor variables
* Normalizing my target variable
* Checking for predictors with the strongest and weakest impacts on price
* Looking at relationships between predictors
* Consistently checking the error

### Baseline Model

Includes only the continuous and discrete numerical values:
* 'bedrooms' 
* 'bathrooms'
* 'sqft_living'
* 'sqft_lot'
* 'floors'
* sqft_above'
* 'yr_built'
* 'yr_renovated'
* 'lat'
* 'long'
* 'sqft_living15'
* 'sqft_lot15'
* 'month_sold'
* 'year_sold'

#### Metrics
* **Adjusted R-squared**: 60.68%

* **Error**: _MAE_: 91417.36 USD, _RMSE_: 120635.48 USD
![baseline_model_.png](https://github.com/jordanate/phase-2-project/blob/main/images/baseline_model_.png)

### Final Model

The final model, Model 7, includes existing columns from the original dataset as well as new/encoded columns:                                         

**Existing columns**:                                                       
* 'bedrooms' 
* 'bathrooms'
* 'sqft_living'
* 'sqft_lot'
* 'floors'
* sqft_above'
* 'yr_built'
* 'lat'
* 'long'
* 'sqft_living15'
* 'sqft_lot15'

**New columns**:                                    
* 'basement' where '0' = No basement and '1' = Yes basement                   
* 'renovations' where '0' = Has not been renovated and '1' = Has been renovated               

**One Hot Encoded columns**:
* 'zipcode' which has 68 columns and 1 reference category
* 'waterfront' which 1 column ('waterfront_YES) and 1 reference category ('waterfront_NO')             
* 'month_sold' which has 11 columns (2 (February) - 12 (December)) with 1 column (1 (January) as the reference category                               
                    
**Ordinal Encoded columns**:                            
* 'view' which ranks the quality of the view on a 0-4 scale                 
* 'grade' which ranks the overall grade of the house on a 0-7 scale             
* 'condition' which ranks the overall condition of the house on a 0-4 scale               

#### Metrics
* **Adjusted R-squared**: 85.51%

* **Error**: _MAE_: 52423.22 USD, _RMSE_: 74226.45 USD 
![model_7.png](https://github.com/jordanate/phase-2-project/blob/main/images/model_7.png)

## Regression Results

In this section, I evaluate my model under the 4 assumptions of linear regression and interpret the coefficients with the strongest impact on price.

The 4 assumptions of linear regression are as follows:
* Linearity   
* Independence (Multicollinearity)     
* Normality (of residuals)      
* Equal Variance (Homoscedasticity)   

### Checking for Linearity
![regression_plot.png](https://github.com/jordanate/phase-2-project/blob/main/images/regresion_plot.png)

The regression plot shows an overall linear relationship between the true price values and the predicted price values thus indicating that the model is relatively accurate.

### Checking for Independence (Multicollinearity)

To check for multicollinearity, I use VIF (Variance Inflation Factor). When using VIF, the general rule is that a value of 5 or higher indicates that multicollinearity with the given variable exists. 

After creating a table of VIF values, I find that 49 of the 99 features in the final model have a VIF value of > 5 which indicates that for each of these variables, multicollinearity with another variable(s) exists. While this is problematic, it is important to note that I was aware of some of the high correlations between predictors in my model (as seen in Model 2), but due to the decreased error that occurred with the inclusion of such predictors, I decided to keep them in my final model. Similarly, with the incorporation of polynomial features, multicollinearity is expected, but again, the inclusion of these features decreased the error of my final model.

Additionally, some of the predictors in my models are inherently related such as latitude, longitude, and various zip codes as well as the square footage of the whole house and the square footage of the house above ground (i.e. not including the basement)

Nevertheless, multicollinearity is a violation of one of the 4 assumptions of linear regression, and therefore, it is crucial to proceed with caution when drawing conclusions on the basis of these predictors.

### Checking for Normality of Residuals
![qq_plot.png](https://github.com/jordanate/phase-2-project/blob/main/images/qq-plot.png)

This Q-Q plot indicates that the residuals are normally distributed, and thus, the model does not violates the assumption of normality.

### Plotting residuals and checking for Homoscedasticity
![resid_plot_.png](https://github.com/jordanate/phase-2-project/blob/main/images/residual_plot_.png)

This residual plot indicates that overall the residuals are homoscedastic (i.e. the relationship appears linear and for the most part, there is no fanning of the points). Nevertheless, it is significant to note that as the price predictions increase past the price of around 850,000 USD, the points begin to fan out indicating a potential problem. Therefore, when the model predicts a price larger than 850,000 USD, it is important to take into account this short-coming of the model.

### Interpreting Strong Predictors of Price

#### Waterfront (predictor name: 'waterfront_YES)

Compared to houses that are not on a waterfront, we see an associated increase of about 67.37% in price for houses that are on a waterfront.

![price_x_waterfront.png](https://github.com/jordanate/phase-2-project/blob/main/images/price_x_waterfront.png)

_Note_: The graph above does not depict an _exact_ 67.37% increase.

#### Latitude and Longitude (predictor names: 'lat' and 'long)

For every increase in 1 standard deviation of latitude, price increases by 22%. Similarly, for every increase in 1 standard deviation of longitude, price decreases by 19.14%.

![price_x_lat-long.png](https://github.com/jordanate/phase-2-project/blob/main/images/price_x_lat-long.png)

_Note_: Increase latitude means going more north, and increase in longitude means going more east. Therefore, the most expensive houses should be in the northwest of King County and the least expensive houses should be in the southeast of King County.

## Conclusions

### Recommendations

#### Stakeholders' criteria
Budget: **$250000**                                               
Floors: **1**                                            
Square Feet of House: **2000 SF**                                            
Square Feet of Lot: **6000 SF**                                            
Bedrooms: **3**                                            
Bath: **2**                                            
Basement?: **No**                                            
Condition (0-4): **Good (3)**                                            
Grade (0-7): **Good (4)**                                            
View Quality (0-4): **None (0)**                                            
Preferred Month of Purchase: **March**                                            
Waterfront?: **No**                                            
Renovated?: **No**                                            
Year Built: **No year in particular**                                            
Square Feet of Neighbors’ Houses: **No specific square footage**                                            
Square Feet of Neighbors’ Houses Lots: **No specific square footage**                                            


#### Question
In which zip code should the stakeholders purchase their home based on the criteria listed?

#### The zip codes and predicted prices for a home of the given criteria are as follows:
Zip code 98032: **$182,296**              
Zip code 98168: **$195,324**              
Zip code 98002: **$181,858**             

These prices are all within the stakeholders' range, but the error of the model is plus or minus $52,423 on average

While all of these prices are still under $250,000 when adding the error, the safest decision would be to aim for a house in the zip code 98002 as it has the lowest predicted price. Furthermore, if the stakeholders decide to pursue a house in the zip code 98002 and indeed end up paying less than their budget, they can use the rest of the money in their budget to purchase a swing set or tree house for their grandchildren.

### Limitations

* A major limitation of my model is the **recency of data**. As I mentioned, the data in this project comes from house sales in King County, Washington from 2014-2015. Therefore, my model is missing 7 to 8 years of information in regard to the evolution of real estate. Furthermore, COVID-19 had major impacts on real estate trends, but unfortunately, such patterns cannot be represented through my model. If possible, I would like to access more recent information about house sales in King County, Washington to improve my model.

* As mentioned earlier, two other issues with my models are that there is some multicollinearity between predictors in my model as well as heteroscedasticity with higher price predictions.

### Next Steps

In addition to adding in more recent data to my model, potential next steps could be analyzing data about nearby parks, restaurants, hospitals, and place of worship (ex: Synagogues, Churches, Mosques) and then incorporating such information into the predictive model. For example, if the stakeholder wanted a house within 5 miles of a hospital along with all of the criteria listed above, I could use the improved model to predict the price of such a house. It would also be important to investigate the level of crime in each zip code and factor this into the model as well. Some questions that this might bring about are, "What level of crime categorizes a neighborhood as unsafe? Does a high level of crime decrease the price?"

## For More Information

For a full analysis, please look at my [Jupyter Notebook](./phase-2-project-notebook.ipynb)
<br /> For a more concise summary, please review my [presentation](https://github.com/jordanate/phase-2-project/blob/main/presentation.pdf)

<br />
For any additional questions, please contact Jordana Tepper at <a href="mailto:jtepper724@gmail.com">jtepper724@gmail.com</a> 

## Repository Structure:

```
├── README.md                           
├── phase-2-project-notebook.ipynb   
├── Phase 2 Project Presentation.pdf         
├── data                                
└── images    
