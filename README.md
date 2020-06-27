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

* Our source data is already been splitted into `train_v2.csv` (23.67 GB) adn we upload the csv file into our S3 bucket.
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

* Several columns we got from the json transformation have a object datatype, therefore, we convert them into proper format like datetime or numeric. 
    ```
    Before Conversion

    date                         int64
    totals.hits                  object
    totals.pageviews             object
    totals.transactionRevenue    object
    
    After Conversion

    date                         datetime64[ns]
    totals.hits                  float64
    totals.pageviews             float64
    totals.transactionRevenue    float64
    ```


### Model

## Results and Conclusions

## Challenges

1. The very fisrt challenge is how to handle with these 4 json type columns in our csv file.

2. 

## Future Work

## Division of Labor

* Zili Bu
    - Project Writeup format
    - Data Preparation and clean
    - Exploratory Analysis
* Hsin-Yu Chen
    - Model
* Huang-Chin Yen
    - Data Source
    - Data Preparation and clean
    - Exploratory Analysis
* Kexin Zhang
    - Model


## Takeways From the Course
* We are able to get familiar with github, for example, how to connect github, create and clone repositories, and how to update our work to a repo in github. 
* The practise of regular express help us to extract desired string from certain text files.
* The experience to work with AWS platform is great. We learn to create clusters and use HDFS to perform map and reduce function towards file in HDFS or S3.
* 