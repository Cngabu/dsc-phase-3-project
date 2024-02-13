# Predicting the Functionality of  Tanzanian Water Wells

![Alt text](https://github.com/Cngabu/dsc-phase-3-project/blob/main/images/Tanzania%20Water%20Wells.jpg)

## Overview

39% of Tanzanians do not have access to basic water supply. Installation of wells by the Tanzanian government, foreign donor organizations, churches and faith-based organizations, and even the villagers has been a frontline measure in trying to resolve the water crisis in Tanzania. Some of the installed wells however cease to function over time while others remain in dilapidated conditions needing repair. Monitoring the wells to ensure they remain functional is imperative in ensuring the benefits achieved by the well installations are not lost. As representatives of an NGO contracted by the Tanzanian government to guide in well maintenance and repair, we sought to come up with a model that can predict the functional status wells in Tanzania. This should help direct stakeholders and policy makers to areas where help in maintenance and repairs is needed. 

## Business Problem

Extensive installation of wells has been carried out to end the water crisis in Tanzania. Hpwever, there is lack of reliable infrastructure for monitoring and maintaining water wells. This leads to inefficiencies in resource allocation and delays in addressing non functional wells and functional wells that need repair. The traditional approaches in management of wells are ineffective as a high proportion of installed water wells cease to function over time while others remain in dilapidated conditions needing repair for a long time. There is need for stakeholders and policy makers to be able to know which wells are likely to be non functional or to need repairs, so they can focus their attention and resources there. 

## Data and Methods

The data used for the modeling was accessed from DrivenData Labs. It consists of 59,400 records and 41 features describing various aspects of the wells such as geographical location, year of constuction, funders and installers, water quality, quantity and source type, and management of the wells amongst other features. 

The data was first cleaned and the dimensions of the categorical columns reduced. We then engineered a new feature. In total ,we used the following 16 features for modelling. 
- **status_group** - Funtionality status of the well
                     A ternary variable with three categories, functional, non-functional and functional needs repair. 
- **amount_tsh** - Total static head (amount water available to waterpoint)
- **funder** - Who funded the well
- **gps_height** - Altitude of the well
- **basin** - Geographic water basin
- **region** - Geographic location
- **population** - Population around the well
- **public_meeting** - True/False
- **permit** - If the waterpoint is permitted
- **extraction_type_group** - The kind of extraction the waterpoint uses
- **management** - How the waterpoint is managed
- **payment_type** - What the water costs
- **water_quality** - The quality of the water
- **quantity** - The quantity of water
- **source** - The source of the water
- **waterpoint_type_group** - The kind of waterpoint
- **age_of_well** - New feature calculated from construction year and date of recording representing well age at the point of data    collection. 

We first conducted exploratory data analysis. For modeling, we chose classification models because our target variable was categorical, consisting of three classes. We built several machine learning models to predict well functionality using logistic regression, Decision Tree Classifier, K Nearest Neighbors, Bagged Trees and Random Forest. Each model was fitted with default hyperparameters and then again with tuned hyperparameters. We used training and validation accuracy to compare models to select the best performing model. 


## Findings

The tuned random forest model was selected as the best model as it has the best accuracy scores with a training accuracy score of 0.894 and the highest validation accuracy score of 0.750. It also had less overfitting than the models that performed better on the training set accuracy. 


![Alt text](https://github.com/Cngabu/dsc-phase-3-project/blob/main/images/Random%20Forest%20Model.png)

The most important features in predicting well function as depicted by our final model were

1. Altitude of the well (gps_height)
2. Well age (age_of_well)
3. Population (population)

Well projects funded by the Government of Tanzania and the Ministry of Water are more likely to be non functional. 

Mtwara and Lindi Regions stand out for having a higher proportion of non-functional wells compared to the functional wells. Ruvuma/Southern Coast and L. Rukwa basin also have a higher proportion of non functional wells compared to the functional ones. 

Well projects where people do not pay for well use or the payment details are unknown, and where public meetings are not held, have a higher proportion of non functional wells compared to the functional wells.  

Well projects that are older have a higher proportion of non functional wells than the ones that are recent(0 - 15 years). 

Dry wells, wells with salty water and wells with dam and lake as a source were more likely to be non-functional. 


## Recommendations

Well projects being funded by the government and its ministry should be thus be closely monitored during the installation and followed closely to ensure continued function

Mtwara and Lindi Regions and wells in Ruvuma/Southern Coast and L. Rukwa basin should be prioritized in repair of non functional and functional wells that need repair.

Introduce and promote well fees and public meetings to enhance community ownership which will translate to better maintenance and follow-up of wells. The money generated from the fees can aid in maintenance and repairs in a timely manner.

Older wells, dry wells and wells with salty water should be monitored more closely as they are more likely to fail 


## Next Steps

**Further hyperparameter tuning:** Hyperparameter tuning can be explored further using GridSearch to further improve on the models used in prediction. 

**Exploring more model types** Model types such as XGBoost, Adaboosting, Naive Bayes, SVM and model stacking that were not used here can be explored to find a better performing model. 

**More Information on Data Features** Some symbols and abbreviations used in the data are not universal. More information on the data can enhance the data cleaning process especially in the funders and installers features to enhance the cleaning process and consequently the model outputs. 






