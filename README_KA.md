# Modeling House Sales in King County, WA


## Introduction
In this project, I was given a csv dataset for house sales in King County, WA to optimize a multiple linear regression model to predict house sale price. The original dataset contains 21596 rows with 21 columns, which includes home ID (notably not a unique key since a home could be sold more than once in this period), sale date, and price (our target dependent variable.

The libraries I used: 
* pandas for data analysis
* numpy for scientific computation
* matplotlib and seaborn plotting
* statsmodels and sklearn for modelling
* folium, bokeh and pyplot for creating geographic visualizations

## Objective / Questions
In addition to creating several versions of the model, I chose three questions to answer from this dataset, and relied on visualizations to help me explore the data and answer my questions, assuming that this is a database being used by a Real Estate agent I am asking questions that I would consider relevant to a potential homebuyer.

1. Given my budget, how can I anticipate house sale prices and house availability depending on whether I am looking to buy a starter home (2/3 bedrooms) versus a multi-generational home (4+ bedrooms)?
2. What can I expect the square footage of the house and lot to be for a home that is older/newer?
3. In what areas were the highest-value homes sold? Are there areas with a higher density of house sales in this period?


## Data Cleaning 

Before proceeding with the visualizations, I conducted the below steps to ensure that I had a complete dataset. 
* adjusted incorrect datatypes (for ‘date’, from object to datetime and for ‘sqft_basement’, from object to float)
* filled missing values (for ‘waterfront’, ‘view’, and ‘yr_renovated)
* checked for duplicate rows
* dropped multicollinear/un-necessary row (‘sqft_living')
* dropped rows that contained outliers in any variable with a z-score of 3

This left me with 20,064 rows of data, and 18 dependent variables.

## Data Visualization

### Bedrooms and Price per Square Foot

In order to answer my first question, I created a boxplot of the price per square foot for each number of bedrooms. As I had removed outliers from this column with a z-score above 3, the highest number of bedrooms in my dataset is 6. 
![Price Per Square Foot Based on # of Bedrooms](dsc-mod-2-project-v2-1-onl01-dtsc-ft-012120/Bdrooms_1.png)

As we can see from the boxplot, there is a definite economy of scale up until we hit 4 bedrooms, at which point the price per square foot begins to increase. It is clear as well that purchasing a one-bedroom house is will almost certainly not be economical per square foot, and you can pay upwards of $800 per foot, higher than any other house size. 

![Number of Home Sales By Price Point Based on # of Bedrooms](dsc-mod-2-project-v2-1-onl01-dtsc-ft-012120/Bdrooms2.png)

We can also see from this facet plot of histograms that over this period the most homes were sold that had 3 or 4 bedrooms. I limited this to only 2-5 bedrooms as there were very few homes sold over this time period that had 1 or 6 bedrooms. If one is in the market for a 4 bedroom home, there may be more supply across various price ranges, but note that there may be many other buyers in the market for homes around this size.


### Square Feet of Lots and Houses (Above Ground)

I next wanted to look at what how the square feet of homes and their lot sizes changed throughout the decades, based on the Built Year of the home.  

![Number of Home Sales By Price Point Based on # of Bedrooms](dsc-mod-2-project-v2-1-onl01-dtsc-ft-012120/TotalSqft1.png)

