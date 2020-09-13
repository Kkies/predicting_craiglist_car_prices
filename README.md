## Introduction

When we want to sell used cars, one of the biggest problems is deciding reasonable selling prices for the cars. An effective way to solve this problem is to use a machine-learning model that can predict car prices.

We used Python code and libraries to build a price-prediction model. The project is an implementation of the project Predicting the Prices of Used Cars.

The goal of this project is to explore the dataset and discuss some interesting observations through visualizations and train machine learning models to fit and predict the prices of the used cars using supervised learning.


## Libraries Used:

To assist us in our research, we utilized the following libraries:

- Pandas - data cleaning and analysis
- Matplotlib - data visualization
- Seaborn - data visualization
- Numpy - data cleaning and analysis
- Math - data analysis
- Random - data cleaning and analysis
- Pickle - data transfer and storing
- statsmodels.formula.api - to create a model from a formula and dataframe.  
- Plotly.express - data visualization
- Re - regular expression searches


## Project objectives

The main objectives of this project are as follows:
Data collection and cleaning
Analyzing the data
Identify relevant machine-learning algorithms for the project.
Build price-prediction models based on the chosen algorithms.
Validate the models.
Identify the most appropriate model.

## Dataset: "Used Cars Dataset"

We used Kaggle dataset for this project. The data comes from Craigslist in the USA and provides information on car sales. It contains more 500.000 vehicles and has 25 columns.

#### Data Columns:

- identry: ID
- url: listing URL
- region: craigslist region
- region_url: region URL
- price: entry price
- year: entry year
- manufacturer: manufacturer of vehicle
- model: model of vehicle
- condition: condition of vehicle
- cylinders: number of cylinders
- fuel: fuel type
- odometer: miles traveled by vehicle
- title_status: title status of vehicle
- transmission: transmission of vehicle
- vin: vehicle identification number
- drive: type of drive
- size: size of vehicle
- type: generic type of vehicle
- paint_color: color of vehicle
- image_url: image URL
- description: listed description of vehicle
- county: useless column left in by mistake
- state: state of listing
- lat: latitude of listing
- long: longitude of listing

## Data Cleaning and Feature Selection:

Dataset has so many missing value in almost all variable, except for a few. Many columns have nothing to do with the prices of the car, such as "id", "url", "image_url", se we removed those columns. We wanted to fixed missing values, because it is important to be handled as they could lead to wrong prediction or classification for any given model being used. We removed outliers and zero value of the price column. As locations do not have major correlation to the prices, we choose to remove 'long' and 'lat' as well. Since it is difficult to impute accurately we dropped columns that didn't have a year or odometer value because they are both heavily correlated to the other and are both missing. We also dropped model column in the end since the information was close to manufacture column, it had many missing values, and it was very difficult to find the value. We did not start droping columns in the beginning because we needed them to determine the missing value for the other columns with missing values so we imputed missing values and used np.select function.  

Since we had many missing value we used np.select function using the key words that we are looking for, then we imputed for the remaining missing values. For example for manufacturer column we used np.select from the describtion column since we could find our missing value answers in the descriptions. We also toke the same approach for the odometer column, but for odometer we choose values between 250 and 300,000 becasue they were many dirty values and missing information. We took the same approach for the year column and age to determine the avreage odometer for that car. For the paint column we imputed the color values from manufacturer coloumn to replaced are missing values. Again we used the same approch for vehicle cylinders, transmission, drive, fuel, size, type, and condition. For VIN column we changed it categorical value to 0 and 1 stating that if it has a VIN number or not.

For our feature engineering we used description column to find cars that is used for parts, project, or it is for purchase cars. 

## Analysis

The prices don't differ very much in each states in the US. But we do find that the used car prices are slightly higher in the states neighboured on Canada (such as Alaska, Idaho, Washington, Montana, North Dakota). 

Higher odometer tends to have lower prices, while lower odometer tends to be more expensive. 

Pickup cars and trucks have higher prices as they cost higher for new. The prices for sedan, wagon, hatchback and mini-van are more stable.

![Price_car_type](https://user-images.githubusercontent.com/62824675/93013192-f6851500-f55a-11ea-92e0-a673f413bc50.png)

The highest median resale price belongs to pickup trucks, followed by trucks. Coupes, vans, and SUVS have lower median resale prices than the trucks. Pickup trucks and trucks also have the largest spread of resale prices.



![Manuf_Count](https://user-images.githubusercontent.com/62824675/93013496-e28ee280-f55d-11ea-906f-60abffff093c.png)
The most popular car manufactore were Ford, Chevrolet, Toyota, Honda, and Nissan




![Unknown](https://user-images.githubusercontent.com/62824675/93013502-f76b7600-f55d-11ea-985b-4d54274b594b.png)
The most popular color is w that most popular color white folowed by black and silver


there is a significant difference between vehicle color by states
there is a significant difference between car manufacturer by states
there is a significant difference between paint color by vehicle condition
there is a significant difference between price by states.



## Conclusion

New and like-new cars tend to be more expensive, while cars with fair and salvage conditions tend to be much cheaper. Cars with 6, 8 or 10 cylinders tend to be more expensive, while 4 and 5-cylinder cars are cheaper. Diesel cars are more expensive than gas and hybrid cars. Cars equipped with all-wheel drive tend to be more expensive than those with front-wheel drive.

Possible Business Questions

Highest price based on type of car
Highest price based on manufacturer of car in 2010
Trend manufacturer base on type=sedan in 2010
How many production of cars type in 2010?
How many type of cars?
How many county_fips for car with 6 cylinder engine?
Manufacturer based on price
