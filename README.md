*UCB-ML-11.1*

## What Drives the Price of a Car? Jupyter Notebook

Analysis Notebook: https://github.com/aditwal/UCB-ML-11.1/blob/main/used_car_value.ipynb

Overview

This analysis was performed to help a used car dealership to find out what consumers value in a used car. We used a dataset on sales of used cars available on kaggle. We utilized CRISP-DM approach for data mining and various regression techniques to develop a model that predicts the price of the used cars. Based on the model, we provided recommendations to the used car dealership.


Business Objectives

1. Background: Used car dealer would like to limit the inventory to the cars popular among buyers. 

2. Goal: Understand what factors make a car more or less expensive 

3. Success Criterion: Reliable and clear recommendation to the client (an used car dealership) as to what consumers value in a used car

Situation Assessment 

1. Inventory of Resources:

    (a) Dataset from Kaggle with selling price of the car and its features.

    (b) Python libraries: Pandas, NumPy, seaborn, plotly, sklearn etc. 

    (c) Regression algorithms taught in class
    
    (d) Class lectures, codio activities, try-it activities

2. Requirements, Assumptions, and Constraints:

    (a) Client is not specialized used car dealer i.e. doea not deal with ultra-luxury, off-road, buses, parts, or salvage cars. 

    (b) Client location is irrelevant/unknown and suggesting best place to sell an used car is out of the scope.

3. Risks and Contingencies terminology:

    (a) Lack of experience of personnel in model building and performing the analysis

    (b) Lack of latest data after pandemic which had significant impact of car prices and how people buy cars

    (c) Lack of computational resources to analyze such a large dataset. 

4. Costs and Benefits:

    (a) Limiting the inventory to cars popular among buyers would help the client sell cars faster

    (b) This would reduce the operational cost as well as improve cash flow to buy new inventory which would lead to more profitability. 

    (c) There are only human resource cost as the data is available free on Kaggle.  

Data Mining Goals

1. Data Problem Definition: Develop a regression model to predict an used car price using information/features available in the dataset and get feature importance

2. Data Mining Success Criteria：The regression model predicts the car prices in the test dataset within a reasonable MSE in order to get reliable feature importance

Preliminary Project Plan: 
1. Project Plan: Following CRISP-DM approach -

    (a) Data understanding: Explore and analyze the available dataset using visualization techniques

    (b) Data preparation: Remove unncessary columns and rows with null values and create a clean training, validation and test dataset 

    (c) Modeling: Train predictive models using algorithms in resource inventory and perform hyperparameter optimization using validation loss

    (d) Evaluation: Determine predictive on test dataset and determine feature importance

    (e) Deployment: Determine how features affect car prices and provide recommendations

2. Initial Assessment of Tools and Techniques - 

    (a) Regression algorithms taught in class - Linear regression, Ridge, Lasso from sklearn
    (b) Techniques taught in class: correlation matrix, sklearn Pipeline feature


Observations and conclusions from data mining steps

1. There are 426880 rows with 18 columns in the dataset. Since 'id' and 'VIN' are definitely random identifiers for a car, they don't have any relevance to the price of the car.  

2. Standard deviation in odometer and price is too high compared to 1st and 3rd quantiles due to few outliers. Restricing price to less than $100000 as beyond that price we venture into ultra-luxury cars whic only specialized car dealers sell. Similarly, filtering out very old cars which might be vintage and skew the model would yield better model. Moreover, we can remove cars with very high mileage which very few passenger cars can achieve. Both year and odometer seem to have an effect on the price.

3. Features for predicting *price* of the car available in the dataset fall in the following categories - 

    (a) Location: region, state

    (b) Car features: cylinders, fuel, transmission, drive, size, type, paint_color, manufacturer, model

    (c) Car history: year, condition, odometer, title_status, manufacturer, model

4. *Region* and *State* can be excluded from the feature list as client location is unknown and we can assume that suggesting best place to sell an used car may be out of scope for this analysis. 

5.  The model of the car is determined by most of the other car features, hence they are not independent. Therefore, the car model can be ignored from the analysis. 

6. Assuming non-specialized used car dealership as client, new and salvage cars, vehicles of type offroad and bus. Cars with title status except 'clean' would have lower price with all other things equal and may cause problems in model training.


Final Model

A regression model based on Ridge method with Lasso method serving as column selector provided the best predictions of the car price in the test dataset. The root mean squared error (RMSE) for the model was around $5000. 

The accuracy of the model is less than desirable. However, predictions show good linearity. The high RMSE maybe due to ignoring the feature 'car model'. However, including that as a feature exhausted the computational resources available. 

Recomendations to Client: 

Based on the best regression model: 

1. Year and odometer reading have significant impact on the price. 

2. Used cars manufactured more recently have higher selling price, while cars with higher odometer readings sell for a lower price. 

3. Better condition and higher number of cylinders have a positive effect on the price of the car. 

4. Used trucks, pick-ups, convertible, coupe cars have higher selling price compared to used sedan, hatchback and mini-van.

5. 4 wheel drives improve the value of the used cars. 

6. Buyers prefer car manufacturers known for reliability such as Honda, Toyota. On the other hand, Fiat, Chrysler, Dodge negatively impact the selling price. As expected, Luxury car manufacturers like Porche, Lexus, Acura have positive impact on the selling price. 

Shortcomings of the model: 

1. The model did not evaluate the interactions with categorical features. For example, model was unable to evaluate how increase in the Odometer reading affect the price of a Toyota as opposed to a Porche.

2. Hence, the above recomendations need to be examined for accuracy using domain knowledge and past experience. 
