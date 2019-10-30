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

After applying <b> linear interpolation method.</b>

![Screenshot_29](https://user-images.githubusercontent.com/46135898/67839600-d51f6400-fb15-11e9-94d5-572ee74c7b8b.png)


