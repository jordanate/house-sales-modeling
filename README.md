# Phase 2 Project

**By**: Jordana Tepper

## Overview

## Business Problem

Explain your stakeholder audience here

## Data

The data that I use for my projects comes from the a dataset about King County, Washington House Sales in 2014-2015. This source includes information such as square footage, number of bedrooms, number of bathrooms, zip code, number of floors, condition of the house, and quality of view.


## Modeling

### Baseline Model

### Final Model

## Regression Results

The model produced the following prices:

Zip code 98032: $182,296

Zip code 98168: $195,324

Zip code 98002: $181,858

These prices are all within the stakeholders' range, but the error of the model is plus or minus $52,423 on average

While all of these prices are still under $250,000 when adding the error, the safest decision would be to aim for a house in the zip code 98002 as it has the lowest predicted price. Furthermore, if the stakeholders decide to pursue a house in the zip code 98002 and indeed end up paying less than their budget, they can use the rest of the money in their budget to purchase a swing set or tree house for their grandchildren.

## Conclusions

### Recommendations

**Stakeholders criteria**
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


The model produced the following prices:

Zip code 98032: $182,296

Zip code 98168: $195,324

Zip code 98002: $181,858

These prices are all within the stakeholders' range, but the error of the model is plus or minus $52,423 on average

While all of these prices are still under $250,000 when adding the error, the safest decision would be to aim for a house in the zip code 98002 as it has the lowest predicted price. Furthermore, if the stakeholders decide to pursue a house in the zip code 98002 and indeed end up paying less than their budget, they can use the rest of the money in their budget to purchase a swing set or tree house for their grandchildren.

### Next Steps

Potential next steps could be analyzing data about nearby parks, restaurants, hospitals, and place of worship (ex: Synagogues, Churches, Mosques) and then incorporating such information into the predictive model. For example, if the stakeholder wanted a house within 5 miles of a hospital along with all of the criteria listed above, I could use the improved model to predict the price of such a house.

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
