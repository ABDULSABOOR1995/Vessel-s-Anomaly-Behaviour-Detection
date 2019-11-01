# EDA of AIS Data & Building ML Model for Vessel's Anomaly Behaviour Detection
## Overview:
Vessel traffic data, or Automatic Identification System (AIS) data, are collected by the U.S. Coast Guard through an onboard navigation safety device that transmits and monitors the location and characteristics of large vessels in U.S. and international waters in real time. In the U.S., the Coast Guard and commercial vendors collect AIS data, which can also be used for a variety of coastal planning purposes.

The Bureau of Ocean Energy Management (BOEM) and the National Oceanic and Atmospheric Administration (NOAA) have worked jointly to repurpose and make available some of the most important records from the U.S. Coast Guard’s national network of AIS receivers. Information such as location, time, ship type, speed, length, beam, and draft have been extracted from the raw data and prepared for analyses.

So in this project we'll perform some basic exploratory data analysis on AIS data, after that we'll make <b>ML(SVR)</b> model to identify vessel's anomaly behaviour detection.

## Data Source
https://marinecadastre.gov/ais/
We performed analysis on <b>AIS_2017_01_Zone10</b> dataset.
## Explanation:
Now we explain every step of our project in detail with screenshots.

<a id='toc'></a>
## Table of Content:

[1. Exploratory Data Analysis of csv file (January, UTM Zone 10, 2017)](#l1)<br>
[2. Data Cleaning](#l2)<br>
[3. Calculating the track of a vessel (one MMSI represents one single vessel)](#l3)<br>
[4. Build SVR Model to identify vessel's anomaly behaviour detection](#l4)

[Conclusion](#conclusion)

<a id='l1'></a>
## 1. Exploratory Data Analysis of csv file (January, UTM Zone 10, 2017):
First of all, I performed some basic exploratory data analysis on data to achieve certain insights and statistical measures. I also draw visualization by graphing latitude & longitude points onto a map using geopandas & folium library.

![Screenshot_21](https://user-images.githubusercontent.com/46135898/67838628-87a1f780-fb13-11e9-85b6-fc5899ab3fc4.png)

![Screenshot_22](https://user-images.githubusercontent.com/46135898/67838641-8e306f00-fb13-11e9-9b2f-e50ed03a25c2.png)

![Screenshot_23](https://user-images.githubusercontent.com/46135898/67838644-9092c900-fb13-11e9-98bb-8e7aa0ecef2a.png)

![Screenshot_24](https://user-images.githubusercontent.com/46135898/67838648-91c3f600-fb13-11e9-93e1-28c71ff8e773.png)

![Screenshot_27](https://user-images.githubusercontent.com/46135898/67838655-938db980-fb13-11e9-8b6d-66627d6e3c7a.png)

![Screenshot_25](https://user-images.githubusercontent.com/46135898/67838663-95f01380-fb13-11e9-977b-b5de438c44bf.png)

![Screenshot_26](https://user-images.githubusercontent.com/46135898/67838665-97214080-fb13-11e9-9199-372e4678a8e5.png)

<a id='l2'></a>
## 2. Data Cleaning:
After performing data analysis, we clean data to make it good for training. In data cleaning process, We'll fill missing values contained in the data by using linear interpolation method.


![Screenshot_28](https://user-images.githubusercontent.com/46135898/67839598-d355a080-fb15-11e9-940c-8d1a125f5dae.png)

So these are the missing values exist in every column. But after applying <b>linear interpolation method</b> for filling missing data, we have the following result.

![Screenshot_29](https://user-images.githubusercontent.com/46135898/67839600-d51f6400-fb15-11e9-94d5-572ee74c7b8b.png)

<a id='l3'></a>
##  3. Calculating the track of a vessel:
Now We'll calculate track of the top 3 vessels and visualize them, Their MMSI are given below.<br>
1- 367390380<br>
2- 366940480<br>
3- 352844000


![Screenshot_30](https://user-images.githubusercontent.com/46135898/68018086-118bc500-fcba-11e9-84b6-983158f8153e.png)


![Screenshot_31](https://user-images.githubusercontent.com/46135898/68018089-12bcf200-fcba-11e9-9e26-8fcee1a34171.png)


![Screenshot_32](https://user-images.githubusercontent.com/46135898/68018091-13ee1f00-fcba-11e9-8ac5-90751a6b2a3a.png)


<a id='l3'></a>
## 4. Build SVR Model to identify vessel's anomaly behaviour detection:
After doing all of the above data analysis, we'll make ML model to identify vessel's anomaly behaviour detection. We select SVR model to find anomaly behaviour of a vessel.

First we seperate year, month, day, hr & minute from BaseDateTime and join them in track1(dataframe) as feature.

sc#33
sc#34

We have selected <b> SOG </b> as a target variable. So now to find most important features to make best model we'll find correlation of all varibles with SOG. 

sc#35
sc#36

Here we can clearly observe that <b> 'LAT', 'hour','Cargo', 'COG'</b> are the features that are highly corelated with SOG, so we select all of them as training featrures.
sc#37

Then we apply train-test-split on the data for model's training and testing purpose.

sc#38

After all, we'll make SVR model to find anomaly behaviour of vessel.

sc#39

The SVR model that we have created is giving 85% accuracy on test data that is good.

sc#40

Now we plot original data(SVG) & predicted data to analyse the predicted result.

sc#41

Well, Its time to find anomaly behaviour of vessels. To do that, first we find difference between actual and predicted values and make their dataframe.

sc#42

The values having larger difference are anamolous.

sc#43
sc#44
<a id='conclusion'></a>
## Conclusion:
So in this way, we can predict any feature of AIS data and then find anomaly behaviour of any vessel.

