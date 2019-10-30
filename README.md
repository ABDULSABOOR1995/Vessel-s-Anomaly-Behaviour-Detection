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
