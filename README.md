# Google Analytcis Customer Revenue Analysis
## Table of Content
* [Group Member](#group-member)
* [Executive Summary](#executive-summary)
* [Introduction](#introduction)
* [Exploratory Analysis](#exploratory-analysis)
* [Methods](#method)
* [Results and Conclusions](#results-and-conclusions)
* [Challenges](#challenges)
* [Future Work](#futurework)
* [Division of Labor](#division-of-labor)
* [Takeways From the Course](#takeaways-from-the-course)



## Group Member
* Zili Bu
* Hsin-Yu Chen
* Huang-Chin Yen
* Kexin Zhang

## Executive Summary


## Introduction
We found Google Analytics Customer Revenue Prediction dataset from Kaggle. [Dataset Link](https://www.kaggle.com/c/ga-customer-revenue-prediction/overview)

As the website introduced, the 80/20 rule is a prevalent rule for many businesses in the real world. It is important to understand our target customers and attract their willingness to purchase the product at Google Store by coordinating proper marketing promotions. Here are some important questions:
- Which region/continent has the highest customers, or highest revenues? 
- Which type of devices/OS has the highest access? 
- Which channel group has the highest access or revenues? 
- Which weekdays, months have the highest access or revenue?
- Can we build some models to predict the revenues from our customers?

We would like to do some exploratory analysis to understand the 


## Exploratory Analysis

### Distribution of Our Variables

## Methods
### Data Sourced

* Our source data is already been splitted into `train_v2.csv` (23.67 GB) and `test_v2.csv`(7.09 GB). We upload the csv file into our S3 bucket.
### Data Preparation and cleanning

* We have several json formatted columns `device`, `geoNetwork`, `totals`, `trafficSource` in our csv files.  Thanks to the [reference](https://www.kaggle.com/julian3833/1-quick-start-read-csv-and-flatten-json-fields) code, we would be able  to convert them into normal dataframe format so that we can do further analysis.

* We check the null or missing value in each columns of our dataset, and these are the columns with at least one null values. We decide to drop thoes with more than 50% null values since they are not very informative.
```
Total columns at least one Values: 
                                               Total    Percent
trafficSource.campaignCode                    903652  99.999889
trafficSource.adContent                       892707  98.788694
totals.transactionRevenue                     892138  98.725728
trafficSource.adwordsClickInfo.isVideoAd      882193  97.625195
trafficSource.adwordsClickInfo.adNetworkType  882193  97.625195
trafficSource.adwordsClickInfo.slot           882193  97.625195
trafficSource.adwordsClickInfo.page           882193  97.625195
trafficSource.adwordsClickInfo.gclId          882092  97.614018
trafficSource.isTrueDirect                    629648  69.678073
trafficSource.referralPath                    572712  63.377425
trafficSource.keyword                         502929  55.655102
totals.bounces                                453023  50.132407
totals.newVisits                              200593  22.198012
totals.pageviews                                 100   0.011066
```

* Next, we recognize that some columns have only constant value and it is not very helpful for our analysis, and we decide to drop them as well.
```
['socialEngagementType',
 'device.browserVersion',
 'device.browserSize',
 'device.operatingSystemVersion',
 'device.mobileDeviceBranding',
 'device.mobileDeviceModel',
 'device.mobileInputSelector',
 'device.mobileDeviceInfo',
 'device.mobileDeviceMarketingName',
 'device.flashVersion',
 'device.language',
 'device.screenColors',
 'device.screenResolution',
 'geoNetwork.cityId',
 'geoNetwork.latitude',
 'geoNetwork.longitude',
 'geoNetwork.networkLocation',
 'totals.visits',
 'totals.newVisits']
```

* The data type of `date` column is string, we convert them into proper date format through datetime packages.

### Model

## Results and Conclusions

## Challenges

## Future Work

## Division of Labor

## Takeways From the Course