# Machine Learning Project 2
## Quality of life in Swiss cities
In collaboration with **LABORATORY  FOR  HUMAN-ENVIRONMENTRELATIONS IN URBAN SYSTEMS(HERUS)**.
Under the supervision of **Massaro Emanuele**

- Link to the final report: [Report.pdf](https://github.com/rezaho/MachineLearning_2018/blob/master/Report_Quality_of_life_in_Swiss_Cities.pdf)

- Link to the **_Run.ipynb_**: [Run.ipynb](https://github.com/rezaho/MachineLearning_2018/blob/master/Run.ipynb)

# Authors:
Kouh Kamari Hosseini Seyed Reza

Habibollahi Saatlou Forough

Piquet Anthony

Erbacher Pierre


# Introduction
The HERUS ( Human Environment Relations in Urban Systems ) lab
wants to find a new model (or improve their existing model ) that is able to
predict the quality of space indicators of Swiss cities using insurance data of the customers from laMobilière.


# Dataset
The data-set has been provided by the insurance company laMobilère.
This dataset is under confidentiality agreements. It contains 1. The data of thousands of people in Switzerland that subscribed to
laMobiliere insurance, we call this dataset “Datacities” and 2. Indicators about corresponding to each city (there are about
90 indicators for 170 cities in Switzerland) provided by Swiss Statistical Office, from 10 000 people.
The raw dataset ‘Datacities’ contains 25 features and about 670 000 entries.


## Feature Description
* JobState: Status of employment
* Civil: Civil status
* YearOfBirth: Year of birth
* Gender: Gender
* Own/Rent: If own or rent an house
* Lang: Speaking language
* Nation: Nation of origin
* Children0-26: How many children
* Car1Price: Price of the first car
* Car1ClaimsCt5Y: Number of claims for the first car
* Car1ClaimsSum5Y: Sum of money of claims for the firstcar
* Car2Price: Price of the second car
* Car2ClaimsCt5Y: Number of claims for the second car
* Car2ClaimsSum5Y: Sum of money of claims for thesecond car
* CarPremium: Premium class
* HHInsSum: Insured Sum
* Standoffurn: Standard of furniture1The descriptions are
* retrieved from the original data description file
* Rooms: Number of rooms
* BuildInsSum: Insured sum of the building
* Yearofconstr: Year of constructions
* HHaBClaimsCt5Y: Number of claims
* HHaBClaimsSum5Y: Sum of money of claims
* HHandBldPrem: Premium class
* Zip: Zip code of residence
* BFS: BFS number
* City: The city

## Indicator description:
* 11 Transportation indicators
* 29 Population indicators
* 11 Work & Workplaces indicators
* 8 Space and Territory indicators
* 18 Housing indicators
* 9 Finance indicators
* 4 Education indicators

**_Note_** that more details about the explanations of the indicators can be found in the **_swissdatadescription.pdf_** file uploaded alongside the code.

# Usage
In case of access to the data-set, you can use the _Run.ipynb_ file to perform the analysis and reproduce the results.

In this notebook we have included all the steps from preprocessing the data to learning them and training a prediction model. The notebook consists of two main sections:
## Features exploration and selection:

This part is used to explore the raw data-set and select the most
relevant features which is done through the following steps: 
1. Loading raw dataset 

2. Translation:

The categorical values are written in German, we translate in English.

3. Unifomization of unknown values:

We regroup all the value _Na_ or white space under the name _unknown_.

4. Features exploration:

* 4.1 Categorical features:

We look at the number of unknown values for each feature.

* 4.2 Numrical features:

We look at the number of zeroes for each feature.

5. Remove Outliers:

We show the proportion of unknown and meaningless zero values and the distribution to see if the feature is exploitable. If there are too many unknown, we consider the feature as useless and prefer to drop it. We remove rows that are considered as outliers.

6. Creation of dummy Variable and replacing categorical values by number

7. Saving the selected and engineered features

## Normalization and Learning:
In this part, we use the preprocessed data-set generated in the Features exploration and selection part. We do normalization and we try to design a model that can predict the indicators of cities.

This part contains the following steps:

1. Loading the selected features and the indicators from the original dataset

2. Merge dataset with city indicator

3. Split the dataset in training and testing set

4. Group cities by population size (assuming that smaller cities do not have the same model as bigger and more popularized cities)

5. Normalization of the categorized dataset

6. Training the selected model:

In this step, we have used three different models:

* Multilayer Perceptron
* Ridge Regression
* Linear Regression

**_Note_** that the results from the two latter methods were very similar and hence we have only reported the predictions from the first two methods in the report file.

7. Extracting the scores for each indicator

## Parameter Setting:

You can modify these parameters in the learning part:


**Number of cities in each class:** You can change by defining _num_cities_per_class_ as you wish.

**Indicator you want to predict:** You can change the range in the for loop over the file containing indicators and choose different groups of them to predict. Current values are indicator number 50 to indicator number 70:

` for i in range(50,70):
        y = X_Class.iloc[:,i]
        y = preprocessing.scale(y)`



## Output:

You will get the **R^2 Score (scores)** on the test data of the chosen model for all 20 chosen indicators and all the city categories. The mean values of these scores and more detailed results are presented in the report file. 

The output files corresponding to each utilized model are named: **_prediction_results_50to70_mlregressor.csv_**, **_prediction_results_50to70_ridge.csv_**, and **_prediction_results_50to70_linear.csv_**.


## Libraries Used:
Matplotlib

Numpy

Pandas

Scikit-Learn: Preprocessing/ PCA/ RidgeRegression/ MLPRegressor(neuralnet)

## Reproductibility:
In case of access to the original dataset, make sure your libraries have the last version. Just run the notebook **_Run.ipynb_** file.


