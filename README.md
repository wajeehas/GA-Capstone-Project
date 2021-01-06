# GA-Capstone-Project
DS114 - Final Capstone Project

## RETAIL PRICE PREDICTION: A regression analysis to predict retail prices of pre-owned items sold on e-commerce app called Mercari ##

    Goals:
  
  The goal of this capstone project was to predict the retail prices of various pre-owned products sold for the US-based e-commerce marketplace called Mercari. This app is designed for everyday people where they can buy and sell different products ranging from clothes, shoes, electronics, kids toys and many more. The key issue facing users of such apps is deciding what is the optimal price to sell their products for, based on the individuals features of the product such as its condition, its branding and its shipping costs. This can be a tricky decision to make as the sellers would usually use their own judgement or conduct market research to assess what other sellers are selling them for. This can be a time-consuming process and sometimes inefficient. Therefore, in this data science project, my aim was to conduct an in-depth anaylsis of the dataset using various regression modelling techniques to predict prices as accurately as possible, given the features of the dataset. The data was found on Kaggle, which contained over 1.4 million rows and 8 different columns. Features included in the dataset were product name, item condition ID, brand name, shipping information, item description and the category of product. 

I followed through the steps below to achieve my goals:
1. Data Cleaning and Wrangling
2. Feature Engineering
3. Exploratory Data Analysis
4. Encoding Categorical Variables
5. Set Target and Predictor Variables 
6. Chose 3-4 Regression Models to run on the data 
7. Evaluate the models 

        Metrics:
    
  DATA WRANGLING:

 The first and most important step before implementing any models is to ensure that the data is in a clean, concise and suitable format. This helps us not only to clarify the type of data we have at hand, but also transform the data into a visually appealing and insightful format, as well to use machine learning tools to generate beneficial findings. Hence, the first step was to conduct data wrangling, such as dropping or replacing any missing values, converting textual data into a cleaned and uniformed format (includes removing upper case letters, punctuations, special characters, and digits) and dropping unwanted columns.  


   FEATURE ENGINEERING:

 Then, I went on to generating new features from the existing ones. For example, I noticed that nearly half of the products listed did not contain a brand name. Instead of dropping valuable data, I created a new column to indicate the presence or absence of a brand name in order to see whether this had any impact on price changes. I did the same for item description column; for which I also looked at the lengths of item descriptions and their correlation with price. For the category column, I seperated each of the sub categories into four individual columns to better understand the relation between each type of category and how they associate with price. For example, Women/Jewellry/Gold/Necklace can be divided into 4 unique sub categories. Finally, for the price column, I transformed the data by taking the log function of the values, since the distribution of the price was heavily skewed to the right; which would otherwise return us with negative price values (not reflective of the real world; you can not have negative prices). I ended up with 14 features. 


   EXPLORATORY DATA ANALYSIS:

 For Data visualisation, I used Seaborn and Matplotlib packages to be able to represent data in a clear and logical format, to understand the relation between the different features, and extract meaningful insights from them. I used a variety of different visualisations such as boxplots, bar charts, pie charts, scatter plots and distribution charts to represent the data. These helped me to understand which specific features were most likely to cause the most significant changes in price. 


   ENCODING TEXTUAL DATA:

 All types of data needs to be tranformed into numerical format in order for it to be able to be processed via machine learning models. For text and categorical data, encoding methods such as one-hot encoding, countvectoriser, tfidvectoriser, and labelbinarizer can be used. I used these encoding methods to tranform the brand name, item condition, categories 1 to 4, presence or absence of brand name and of item description into numbers/tokens, so they could be inputted into our models. Since the dataset was quite large, it was useful to convert the tranformed data into a sparse matrix as a way to increase memory efficiency. 


   SET TARGET AND PREDICTOR VARIABLES:

 It is important to define what the target variable (y) is and what the predictor variables (X) are. In this instance, the target variable was price log (the transformed price values) since this is what we are trying to predict; and the predictor variables were all the remaining features. I used Standard Scaler to standardise the data, so that it is all on the same scale. Once the data was standardised, I then split my data into a train set and a test set. This was done on the basis of a 80:20 ratio. This means, the model will learn 80% of the data provided and make predictions on the unseen 20% data. The better the model is able to predict prices accurately on unseen data, the more successful our model is. 


   MODELLING:

 This project made use of regression modelling techniques, since what we are trying to predict is a continuous variable, price. The regression models in ran included Linear Regression, Ridge Regression, Random Forest Regressor and Gradient Boosting Regressor. I first fit each of the models on the data, then, obtained the training and test scores, along with the cross validation scores. If the models perform above baseline, then they indicate significant predictability. 


   EVALUATION:

 The baseline for my predictions was 0.012 (mean of the predictor training set). This means that if the cross validation scores are higher than this, then we can say that the models have reasonable level of predictability. However, the main success metric in this project was the 'Root Mean Squared Log Error' (RMSLE) score. RMSLE looks at the relative error between actual and predicted values, and it is a robust measure against extreme outliers. The RMSLE can drastically scale down outliers in data points, and in turn, reducing their effect. The most important reason for using this measure is that RMSLE incurs a large penalty for underestimation of the target variable than the overestimation. In business contexts, this can be very useful, where underestimation of the target variable is not acceptable, however overestimation is accepted. This means that the lower the RMSLE score of each of the models, the better it has performed.    

    Findings:
  
  Below are the training, test and mean cross validation training scores, respectively:
 1. Linear Regression: 0.413, 0.409, 0.407
 2. Ridge Regression: 0.413, 0.409, 0.407
 3. Gradient Boosting Regressor: 0.343, 0.344, 0.343 
 4. Random Forest Regressor: 0.516, 0.457, 0.486
    
In terms of the RMSLE scores, the models scored as follows:
 1. Linear Regression: 0.142
 2. Ridge Regression: 0.142
 3. Gradient Boosting Regressor: 0.149 
 4. Random Forest Regressor: 0.135
    
As seen above, most of the models gave me very similar results; most of the cross validation scores were close to 40-50%, which is performing above baseline. These models have performed quite consistently with each other, which gives us an indication that the models are able to make good predictions to a certain level and in the right direction based on the predictor variables. Based on the train and test scores above, we can see that Random Forest Regressor has performed the best, as compared the remaining models. In terms of the RMSLE scores, we can see again, that Random Forest Regressor has scores the lowest RMSLE score, followed by linear and ridge regression models, and finally gradient boosting. This means that the Random Forest Regressor model made predictions with the lowest relative error rate compared to the rest. 
 
When plotting the actual vs predicted values of each model, it was clear that there is a positive correlation between the actual price values and predicted price values for random forest, linear and ridge regression. On the other hand, predictions were much more scattered around for gradient boosting model.  In conclusion, it can be seen that Random Forest Regressor appears to be the strongest model in terms on predicting the correct prices for different items sold on Mercari, both in terms of train/test scores and RMSLE scores. 

    Limitations/Follow-up:
  
  In terms of the drawbacks of this project, there are many additional features which were not included in the dataset, that could have been very useful in predicting prices. For example, having access to data regarding the ratings recieved for each product, as well as the reviews on the product could have been beneficial in considering what ratings or use of certain words can have an impact on price. In addition to that, as this was a pre-existing dataset, it has lower time validity, meaning that factors accounting for the largest price changes may be different 2 years ago, then they would be today. 

In terms of further actions for this project, I would like to conduct an in-depth natural language processing, such as sentiment analysis and text mining, in order to determing how the use of certain words or phrases in the product name and description can have an impact on price. It would be very interesing to generate and implement a price recommendation system which can be integrated into e-commerce apps such as Mercari and UK-based app called Vinted, to help users determine the best prices for their products. I would like to carry out a similar project with data collected from webscrapping a similar site and see how the findings can be applicable to various retail contexts. The inclusion of further features, such as images and the quality of images can be helpful as well.  Finally, I would like to run further models on the data such as regularization models like Elastic Net and Lasoo Regression, Support Vector Regression, LightGBM and CatBoost Regression models to determine the best model with the highest predictive power.  




