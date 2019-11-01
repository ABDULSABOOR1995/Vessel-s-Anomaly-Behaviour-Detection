# EDA of AIS Data & Building ML Model for Vessel's Anomaly Behaviour Detection
## Overview:
Vessel traffic data, or Automatic Identification System (AIS) data, are collected by the U.S. Coast Guard through an onboard navigation safety device that transmits and monitors the location and characteristics of large vessels in U.S. and international waters in real time. In the U.S., the Coast Guard and commercial vendors collect AIS data, which can also be used for a variety of coastal planning purposes.

The Bureau of Ocean Energy Management (BOEM) and the National Oceanic and Atmospheric Administration (NOAA) have worked jointly to repurpose and make available some of the most important records from the U.S. Coast Guard’s national network of AIS receivers. Information such as location, time, ship type, speed, length, beam, and draft have been extracted from the raw data and prepared for analyses.

So in this project, we'll perform some basic exploratory data analysis on AIS data, after that we'll make the <b>ML(SVR) model</b> to identify vessel anomaly behavior detection.
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

[Conclusion](#conclusion)<br><br><br>

<a id='l1'></a>
## 1. Exploratory Data Analysis of csv file (January, UTM Zone 10, 2017):
First of all, We performed some basic exploratory data analysis on data to achieve certain insights and statistical measures. I also draw visualization by graphing latitude & longitude points onto a map using geopandas & folium library.<br><br><br>

![Screenshot_21](https://user-images.githubusercontent.com/46135898/67838628-87a1f780-fb13-11e9-85b6-fc5899ab3fc4.png)
<br><br><br>

![Screenshot_22](https://user-images.githubusercontent.com/46135898/67838641-8e306f00-fb13-11e9-9b2f-e50ed03a25c2.png)
<br><br><br>

![Screenshot_23](https://user-images.githubusercontent.com/46135898/67838644-9092c900-fb13-11e9-98bb-8e7aa0ecef2a.png)
<br><br><br>

![Screenshot_24](https://user-images.githubusercontent.com/46135898/67838648-91c3f600-fb13-11e9-93e1-28c71ff8e773.png)
<br><br><br>

![Screenshot_27](https://user-images.githubusercontent.com/46135898/67838655-938db980-fb13-11e9-8b6d-66627d6e3c7a.png)
<br><br><br>

![Screenshot_25](https://user-images.githubusercontent.com/46135898/67838663-95f01380-fb13-11e9-977b-b5de438c44bf.png)
<br><br><br>

![Screenshot_26](https://user-images.githubusercontent.com/46135898/67838665-97214080-fb13-11e9-9199-372e4678a8e5.png)
<br><br><br>

<a id='l2'></a>
## 2. Data Cleaning:
After performing data analysis, we clean data to make it good for training. In the data cleaning process, We'll fill missing values contained in the data by using the linear interpolation method.
<br><br><br>

![Screenshot_28](https://user-images.githubusercontent.com/46135898/67839598-d355a080-fb15-11e9-940c-8d1a125f5dae.png)
<br><br><br>

So these are the missing values that exist in every column. But after applying <b>The Linear interpolation method </b>for filling missing data, we have the following result.<br><br><br>

![Screenshot_29](https://user-images.githubusercontent.com/46135898/67839600-d51f6400-fb15-11e9-94d5-572ee74c7b8b.png)
<br><br><br>

<a id='l3'></a>
##  3. Calculating the track of a vessel:
Now We'll calculate track of the top 3 vessels and visualize them, Their MMSI is given below.<br>
1- 367390380<br>
2- 366940480<br>
3- 352844000
<br><br><br>


![Screenshot_30](https://user-images.githubusercontent.com/46135898/68018086-118bc500-fcba-11e9-84b6-983158f8153e.png)
<br><br><br>

![Screenshot_31](https://user-images.githubusercontent.com/46135898/68018089-12bcf200-fcba-11e9-9e26-8fcee1a34171.png)
<br><br><br>

![Screenshot_32](https://user-images.githubusercontent.com/46135898/68018091-13ee1f00-fcba-11e9-8ac5-90751a6b2a3a.png)
<br><br><br>

<a id='l3'></a>
## 4. Build SVR Model to identify vessel's anomaly behaviour detection:
After doing all of the above data analysis, we'll make the ML model to identify the vessel's anomaly behavior detection. We select the SVR model to find the anomaly behavior of a vessel.

First, we separate year, month, day, hr & minute from BaseDateTime and join them in track1(data frame) as a feature.<br><br><br>

![Screenshot_33](https://user-images.githubusercontent.com/46135898/68021223-a7c3e900-fcc2-11e9-8f28-4f16eca47d8b.png)

<br><br><br>

![Screenshot_34](https://user-images.githubusercontent.com/46135898/68021227-a8f51600-fcc2-11e9-8d94-530f51e0f695.png)

<br><br><br>

We have selected <b>SOG</b> as a target variable. So now to find the most important features to make the best model we'll find the correlation of all variables with SOG.<br><br><br>

![Screenshot_35](https://user-images.githubusercontent.com/46135898/68021230-aa264300-fcc2-11e9-9fbb-233abf4867cd.png)

<br><br><br>

![Screenshot_36](https://user-images.githubusercontent.com/46135898/68021231-ab577000-fcc2-11e9-8fb7-c21a7c1d1886.png)

<br><br><br>

Here we can clearly observe that <b> 'LAT', 'hour','Cargo', 'COG'</b> are the features that are highly corelated with SOG, so we select all of them as training featrures.
<br><br><br>

![Screenshot_37](https://user-images.githubusercontent.com/46135898/68021233-ad213380-fcc2-11e9-941a-112273734242.png)

<br><br><br>

Then we apply train-test-split on the data for model's training and testing purpose.
<br><br><br>

![Screenshot_38](https://user-images.githubusercontent.com/46135898/68021234-ae526080-fcc2-11e9-8941-21c957df00d8.png)

<br><br><br>

After all, we'll make SVR model to find anomaly behaviour of vessel.
<br><br><br>

![Screenshot_39](https://user-images.githubusercontent.com/46135898/68021235-af838d80-fcc2-11e9-84d7-b337d47fb9f7.png)

<br><br><br>

The SVR model that we have created is giving 85% accuracy on test data that is good.
<br><br><br>

![Screenshot_40](https://user-images.githubusercontent.com/46135898/68021237-b01c2400-fcc2-11e9-8640-b65ac293a636.png)

<br><br><br>

Now we plot original data(SVG) & predicted data to analyse the predicted result.
<br><br><br>

![Screenshot_41](https://user-images.githubusercontent.com/46135898/68021238-b27e7e00-fcc2-11e9-9c02-cd7b26bb9902.png)

<br><br><br>

Well, Its time to find anomaly behaviour of vessels. To do that, first we find difference between actual and predicted values and make their dataframe.
<br><br><br>

![Screenshot_42](https://user-images.githubusercontent.com/46135898/68021241-b4484180-fcc2-11e9-9eca-4d512d49b9bc.png)

<br><br><br>

The values having larger difference are anamolous.
<br><br><br>

![Screenshot_43](https://user-images.githubusercontent.com/46135898/68021244-b5796e80-fcc2-11e9-9275-c040880b6dac.png)

<br><br><br>

![Screenshot_44](https://user-images.githubusercontent.com/46135898/68021245-b6aa9b80-fcc2-11e9-8fb8-d3001ea97a62.png)

<br><br><br>

<a id='conclusion'></a>
## Conclusion:
So in this way, we can predict any feature of AIS data and then find anomaly behaviour of any vessel.

