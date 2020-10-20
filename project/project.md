# Estimating Soil Moisture Content Using Sensor and Weather Data

## Team
Cody Harris, harrcody@iu.edu, [fa20-523-305](https://github.com/cybertraining-dsc/fa20-523-305), [Edit](https://github.com/cybertraining-dsc/fa20-523-305/edit/master/project/project.md)

{{% pageinfo %}}

## Abstract

As the world is gripped with finding solutions to problems such as food and water shortages, the study of agriculture could improve where we stand with both of these problems. By integrating weather and sensor data, a model could be created to estimate soil moisture based on on weather data. While some farmers could afford to have many moisture sensors and monitor them, many would not have the funds or resources to keep track of the soil moisture long term. A solution would be to allow farmers to contract out a limited study of their land using sensors and then this model would be able to predict soil moistures from weather data.
 
Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** agriculture, soil moisture, IoT

## Topic Discussion

Maintaining correct soil moisture throughout the plant growing process can result in better yeilds, and less overall problems with the crop. Water deficiencies or surplus at various stages of growth have different effects, or even negligable effects[^1]. It is important to have an idea of how your land consumes and stores water, which could be very different based on the plants being used, and variation of elevation and geography.

For hundreds of years, farmers have done something similar to this model. The difference is the precision that we can gain by using real data. For the past few hundred years, farmers had to rely on mostly experience and touch to know the moisture of their soil. While many farmers were successful, in the sense that they produced crops, there were ways they could have better optimized their crops to produce better. The water avaliable to the plants is not the only variable that effects yeilds, but this project seeks to create an accessible model to which farmers can have predicted values of soil moisture without needing to buy and deploy expensive sensors.

The model created could be used in various ways. The first main use is to be able to monitor what is currently happening in the soil so that changes can be made to correct the issue if there is one. Secondly, a farmer could evaluate historical data and compare it to yeilds or other results of the harvest and use this analytical information to inform future descions.

This project specifically seeks to see the effect of weather on a particular piece of land in Washington state. This process could be done all over the world to obtain benchmarks. These benchmarks could be a cheap option for a farmer that does not have the funds to support a full study of water usage on their land. Instead, they could look for a model that has land that has similar soil and or geographical features, and then use their own weather data to estimate their soil moisture content.

## Datasets

The first data set comes from NOAA and contains daily summary data in regards to various measurments such as temperature, percipitation, wind speed, etc. For this project, only data that came from the closest station to the field will be used [^2]. In this case, that is the Pullman station at the Pullman-Moscow airport. Below is an image showing the weather data collection location, and the red pin is at the longitude and lattitude of one of the sensors in the field. This data is in csv format.

<img src="https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/resources/distance_map.png" data-canonical-src="https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/resources/distance_map.png" width="350" height="350" />

The second dataset comes from the USDA. This dataset consits of "hourly and daily measurements of volumetric water content, soil temperature, and bulk electrical conductivity, collected at 42 monitoring locations and 5 depths (30, 60, 90, 120, and 150 cm)" at a farm in Washington state [^3]. Mainly, the daily temperature and water conent are the measurements of interest. There are multiple files that have data that corresponds to what plants are being grown in specific places, and the make up of the soil at each sensor cite. This auxilary information could be used in later models once the base model has been completed. This data is in tab delimited files.

Within the data, there are GIS file types that can be imported into Google Maps desktop to visualize the locations of the sensors and other geographical information. Below is an example of the sensor locations plotted on the sattelite image.

<img src="https://github.com/cybertraining-dsc/fa20-523-305/blob/master/project/resources/sensor_locations.png" data-canonical-src="https://github.com/cybertraining-dsc/fa20-523-305/blob/master/project/resources/sensor_locations.png" width="651" height="280" />

## Data Cleaning and Aggregation

The first step is to get the soil moisture data into a combined format, currently it is in one file per sensor, and there are 42 sensors. See the data_cleaning_aggregation.ipynb file to see how this was done. After aggregation, some basic information can be checked about the data. For instance, there is quite a bit of NAs in the data. These NAs are just instances where there was no measurement on that day. There is about 45% NAs in the measurement columns. To further clean the data, any row that has only NAs for the measurements will be removed.

Next, the weather data needs some small adjustments. This is mostly in the form of removing columns that either are empty or have redundant data such as elevation. 

Once the data is sufficiently clean, some choices have to be made on joining the data. The simplist route would be to join the weather measurements directly with the same day the soil measurement, however, the previous days weather is likely to also have an impact on the moisture. In the same fashion, the weather for the 5 previous days might all have a large impact on the moisture. So simply joining the two data sets right now is likely not the correct course of action until further analysis is made.

## Preliminary Analysis and EDA



## References
[^1]: O. Denmead and R. Shaw, "The Effects of Soil Moisture Stress at Different Stages of Growth on the Development and Yield of Corn 1", Agronomy Journal, vol. 52, no. 5, pp. 272-274, 1960. Available: 10.2134/agronj1960.00021962005200050010x.

[^2]: N. (NCEI), "Climate Data Online (CDO) - The National Climatic Data Center's (NCDC) Climate Data Online (CDO) provides free access to NCDC's archive of historical weather and climate data in addition to station history information. | National Climatic Data Center (NCDC)", Ncdc.noaa.gov, 2020. [Online]. Available: https://www.ncdc.noaa.gov/cdo-web/. [Accessed: 19- Oct- 2020].

[^3]: "Data from: A field-scale sensor network data set for monitoring and modeling the spatial and temporal variation of soil moisture in a dryland agricultural field", USDA: Ag Data Commons, 2020. [Online]. Available: https://data.nal.usda.gov/dataset/data-field-scale-sensor-network-data-set-monitoring-and-modeling-spatial-and-temporal-variation-soil-moisture-dryland-agricultural-field. [Accessed: 19- Oct- 2020].
