# forest-fires
Computer Science Master's degree “Data Mining I" subject project: Analysis of data of Forest Fires in Portugal made in R.
By Matias Luna, Ana Torres & Inês Gonçalves

Open notebook.nb.html to see code of the project.

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
Type of Data
• Tabular
• Nondependency-oriented data

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

Data transformation

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

