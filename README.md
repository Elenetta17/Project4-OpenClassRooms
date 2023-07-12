# Project4-OpenClassRooms
Anticipate building consumption needs

## Business case
To achieve its goal of a carbon-neutral city by 2050, my team is taking a close look at the consumption and emissions of non-residential buildings.

Careful readings were taken by Seattle city officials in 2016. 
However, these readings are expensive to obtain, and from those already made, I want to try to predict the CO2 emissions and the total energy consumption of non-residential buildings for which they have not yet been measured.

I am also trying to assess the interest of the "ENERGY STAR Score"* for prediction, which is tedious to calculate with the approach currently used by my team. I will integrate it into the modeling and I will judge its interest.

Here is a summary of the mission:

-	Perform a short exploratory analysis
-	Test different prediction models in order to best respond to the problem
-	Analysis of the interest of the ENERGY STAR Score

## Main results
Starting from the initial dataset, potentially interesting variables for the modeling were selected: main usage, surface of car park and buildings, district and zip code, year of construction, number of floors and the Energy Star Score. 
Outliers were removed or replaced and missing values were replaced.

Once the dataset was cleaned, several analysis were carried out:

-	Univariate analysis to study the distributions of variables
-	Bivariate analysis to study the relationship between targets and independent variables. Numerical variables do not present collinearity with the targets. Emissions and energy consumption seem to be correlated with the main usage and the ZipCode
-	An analysis of the correlations between the independent variables, which showed that the variables are weakly correlated

After the EDA:

-	the categorical variables were encoded using TargetEncoder
-	several types of regressions (linear with or without regularization, SVR and tree models) were tested
-	the effect of variable transformations was studied
-	the effect of log transformation of the target variable was studied
-	the effect of adding polynomial variables was studied
-	for each type of regression, GridSearchCV was used to tune the hyperparameters and the best model was analyzed

The best model for predicting energy consumption is XGBoost, and the variable that impacts the predictions the most is the product between ENERGY STAR Score and the ratio between electricity consumption and total consumption. This suggests that regardless of the size, number of floors and age of the building, energy performance should be optimized to limit consumption.
The best model for predicting CO2 emissions XGBoost and the variable that most impacts the predictions is the ratio between electricity consumption and total consumption. This suggests that electricity should be favored as energy source to limit emissions.

The ENERGY STAR Score, even if it is not the variable that impacts the model the most, allows to obtain better results. So, it is necessary to keep calculating it. However, the calculation of the ENERGY STAR Score is based on several characteristics of the building, such as size, number of occupants/workers, number of heating or cooling equipment, etc. By having this data and using it for modeling, perhaps it would be possible to obtain better scores without directly using the ENERGY STAR Score.



