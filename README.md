# Welcome to forest-fires repository
Computer Science Master's degree “Data Mining I" subject project: Analysis of data of Forest Fires in Portugal made in R.
By Matias Luna, Ana Torres & Inês Gonçalves

Open notebook.nb.html to see code of the project.

Open DataMiningI-1.pdf to see the Power Point of the project for more details about Visualization and Results.

# About the project

The project's objetive was to appy Data mining techniques to predict the cause of a set of fires that occur in Portugal and, thus, better support the decision to take preventive measures to avoid tragedy. 

The ICFN - Nature and Forest Conservation Institute has a record of the forest fires that occurred in Portugal for several years, which information is located in the file fires_train.csv, where there is data on reported forest fires during 2014 and 2015, for which the cause is known. For each fire, there is information such as the site, the alert date/hour, the extinction date/hour, the affected area and the cause type (intentional, natural, negligent, rekindling or unknown).

This practical assignment aimed to build a machine learning model to predict the cause type of a forest fire: intentional or non-intentional.

Data Understanding and Preparation: This task involves summarizing and visualizing the data to provide valuable insights. Consider questions that could be interesting to check with the available data and provide answers using textual summaries or data visualization. Based on this analysis, you should also check if it is necessary to carry out any data clean-up and pre-processing steps.

Predictive Modelling: From the available data, you should define the data set used for the classification task at hand. Different models should be considered, and the choice of the final model should be justified. 

# Problem Definition
It is a Binary Classification Problem

Original Attributes: "id","region","district","municipality","parish","lat","lon","origin","alert_date","alert_hour","extinct ion_date","extinction_hour","firstInterv_date","firstInterv_hour","alert_source","village_area","veg etation_area","farming_area","village_veget_area","total_area".

Target Variable: "intentional_cause" • 0->no • 1->yes

Output of the Classification Model: probability of a fire being intentional

# Data Understanding

In this step, the data is analyzed in order to understand the type of data, which is Tabular and Nondependency-oriented, but also the type and scales of the attributes, for example:

• id : Numerical and Ratio

• region: Categorical and Nominal

• alert_date: Numerical and Interval

This analysis was performed on all attributes before continuing the project.

# Data Preparation | Data Quality Issues

Missing values

• Variables with some missing values (region, extinction_date, firstInterv_date).

• In the case of alert_source, all the values are missing values.


Inconsistent or incorrect values
• Values of region having “- ”.

• Diferent ways of naming the same district (“Viana do Castelo” and “Viana Do Castelo”).

• The coordinates are not represented in the same way.

• Some of the coordinates values have “,” instead of “.”, which is not used in R.

# Data Cleaning – Handling Missing Values

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/938a3f2c-65bf-4704-b871-b3ae4bbacde1)

# Data Cleaning – Handling Incorrect Values

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/3f3444a8-53d1-44b4-8694-5e193476ee0f)

# Data transformation


• Conversion of all coordinates to the decimal form.


Dimensionality Reduction - Feature Selection

All of these variables were removed because they were irrelevant to the analysis:

• id

• alert_date

• firstInterv_hour 

• extinction_hour 

• alert_source


Feature Engineering

Through the values of the coordinates ("lat" and "lon") and the alert date ("alert_date") a few more variables were added.

• temp (temperatura média)

• tempMax (temperatura máxima)

• windGust (rajada de vento)

• windVelocity (velocidade do vento)


# Data Visualization

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/d7daf438-8225-4fce-ac61-6c8377c8bb0c)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/502ab651-f5ac-4679-b0bf-b0c4b32fbb45)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/4524b8f5-3706-4e1b-8de6-e1935823a15e)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/f021d952-53a3-404f-92fd-a83a8bae63f3)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/091e7535-5b3f-4f23-a3b8-c726cbb30320)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/ce95381a-01e1-42d9-9f7a-a122b5e95741)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/b8d42358-2d4f-41ad-a924-56f63e37fff3)

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/94c9bec0-7aff-4bdf-80a9-da2765da6370)


# Predictive Modelling

• Evaluation Metric: AUC (Area under the Curve)

• Train and Test Split (70% - 30%)

• k-fold Cross Validation

• Applied recipes where:

  + Too Disperse predictors -> removed

  + Categorical predictors -> converted to numeric values

  + Numeric predictors -> centered and scaled

  + Date predictors -> sometimes included (depends on the model) + Variables with large correlations to others -> removed


Best Results

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/4edf2d01-b829-43f8-9f2d-d8edd5819516)

Last Fit

![image](https://github.com/matiasortizluna/forest-fires/assets/64530615/83b85ecd-917b-4884-b27c-b5e25ffa5c19)

# Conclusions, Limitations and Future Work

• The model that achieved the most AUC was Random Forest.

• According to the last fit model, the variables that matter the most (above 25% of importance)

• One of the limitations was making the data tidy and working in the correct formats that the models needed.

• For future work, more variations of features could be selected for other models to produce better results. Also, different tuning of the parameters could be performed.
are: tempMax; total_area; village_area; windGust; vegetation_area.

