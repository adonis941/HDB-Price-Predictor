# HDB-Price-Predictor

This is a joint effort between Darius Ng (Git: https://github.com/spreadjam) & Filbert Koh (Git: https://github.com/adonis941). Both members provided equal contributions to this project.

This project aims to build a HDB price predictor tool using machine learning models to predict the estimated prices of current brand new BTO (Build-to-Order) flats in Singapore when they will be up for resale in 5 years time. Along the way, we aim to also extract value-added insights which could be helpful for anyone looking to evaluate their next flat purchase/sale.

To provide some context, in Singapore, brand new HDB flats built under the BTO scheme will need to be occupied for a minimum of 5 years, also known as the Minimum Occupancy Period (MOP). During the MOP, the flat can neither be put up for rental nor be sold. This is to prevent what is meant as affordable public housing to be used as an investment/income vehicle, which would otherwise drive HDB prices up. The vast majority of HDB flats comes with a 99-year lease; upon expiry of lease, the government will repossess the flat and occupants will have to look for another means of accomodation. In addition, a resale flat are flats which can be sold.

Our dataset contains the details of all resale flat transactions made between from 2017 till current (Dec 2022) and was downloaded from data.gov.sg. The estimated size of the dataset was 142,000 rows with 11 columns.

Data cleaning was performed to check for null & duplicated data. Feature engineering was then performed to convert the columns 'remaining_lease' from string object to a float object expressed in number of years. The column 'month' was also converted to a datetime object.
A new column, 'price_psm', was created to display the price per square metre paid for that particular transaction. Finally, categorical encoding was performed on string columns 'town', 'flat_type' & 'storey_range' to prepare the data for machine learning model training.

Exploratory data analysis was performed on the dataset to extract helpful information which could help interested parties decide or evaluate their choices of resale flats. This was performed using a combination of matplotlib & Seaborn.

Next, we identified the labels which we want to predict, which are resale price & price per square meter. We identified the relevant features which will be used in the prediction of the labels. Finally, we shortlisted 
suitable machine learning models to be evaluated. In essence, we worked with Linear Regression, Lasso & Ridge Regression, ElasticNet, Random Forest, Support Vector Regressor, Gradient Boosting model & XGBoost. All models were evaluated using RMSE & R2 score as evaluation metrics.

In essence, for Resale Price prediction, XGBoost outperforms all other models in performance and processing speed. For Price per Square Metre prediction, a tuned version of Gradient Boosting outperforms all other models in raw performance metrics; however, XGBoost outperforms Gradient Boosting greatly for processing speed with a slight disadvantage in performance.

Ultimately, XGBoost was chosen as the model to be used in the Resale Price prediction tool while GB was chosen for Price per Square Metre as the team would like to focus more on accuracy considering that transacting a flat is a major event in a person's life.
These 2 predictors make up the HDB Price Predictor tool and can be altered for use for older flats.


