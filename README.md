# Phase 2 Project

![king_county_.jpg](https://github.com/jordanate/phase-2-project/blob/main/images/king_county_.jpg)

**By**: Jordana Tepper

## Overview

## Business Problem

An elderly couple, Bruce and Carol, are from King County, Washington and want to downsize from their current home as there is no need for them to deal with the maintenance of a large house anymore. Nevertheless, in the past few years, Bruce and Carol have become grandparents and want a home in which there is enough room for their two grandchildren to sleep over and play outside. Bruce and Carol have a set criteria for what they want in a house but do not know where in King County they should look to fulfill such preferences.

Therefore, the goal of this project is to build a predictive model based on real data from house sales in King County, Washington that can answer the following question: **In which zip code should the stakeholders purchase their home based on the criteria listed?**

## Data

The data that I use for my projects comes from a dataset from Kaggle about King County, Washington House Sales in 2014-2015. This source includes information such as square footage, number of bedrooms, number of bathrooms, zip code, number of floors, condition of the house, and quality of view.

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
![baseline_model.png](https://github.com/jordanate/phase-2-project/blob/main/images/baseline_model.png)

### Final Model

The final model, Model 7, includes existing from the original dataset as well as new/encoded columns:                                         

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
* ![model_7.png](https://github.com/jordanate/phase-2-project/blob/main/images/model_7.png)

## Regression Results

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

A major limitation of my model is the **recency of data**. As I mentioned, the data in this project comes from house sales in King County, Washington from 2014-2015. Therefore, my model is missing 7 to 8 years of information in regard to the evolution of real estate. Furthermore, COVID-19 had major impacts on real estate trends, but unfortunately, such patterns cannot be represented through my model. If possible, I would like to access more recent information about house sales in King County, Washington to improve my model.

### Next Steps

In addition to adding in more recent data to my model, potential next steps could be analyzing data about nearby parks, restaurants, hospitals, and place of worship (ex: Synagogues, Churches, Mosques) and then incorporating such information into the predictive model. For example, if the stakeholder wanted a house within 5 miles of a hospital along with all of the criteria listed above, I could use the improved model to predict the price of such a house. It would also be important to investigate the level of crime in each zip code and factor this into the model as well. Some questions that this might bring about are, "What level of crime categorizes a neighborhood as unsafe? Does a high level of crime decrease the price?"

## For More Information

For a full analysis, please look at my [Jupyter Notebook](./phase-2-project-notebook.ipynb)
<br /> For a more concise summary, please review my [presentation]

<br />
For any additional questions, please contact Jordana Tepper at <a href="mailto:jtepper724@gmail.com">jtepper724@gmail.com</a> 

## Repository Structure:

```
├── README.md                           
├── phase-2-project-notebook.ipynb   
├── Phase 2 Project Presentation.pdf         
├── data                                
└── images    
