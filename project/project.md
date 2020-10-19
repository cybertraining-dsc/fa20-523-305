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

The first data set comes from NOAA and contains daily summary data in regards to various 

<img src="https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/resources/distance_map.png" data-canonical-src="https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/resources/distance_map.png" width="400" height="400" />
![Map showing distance between weather data collection and farm](https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/resources/distance_map.png "Distance Map" =300x300)


## References
[^1]: O. Denmead and R. Shaw, "The Effects of Soil Moisture Stress at Different Stages of Growth on the Development and Yield of Corn 1", Agronomy Journal, vol. 52, no. 5, pp. 272-274, 1960. Available: 10.2134/agronj1960.00021962005200050010x.
