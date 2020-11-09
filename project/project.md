# Estimating Soil Moisture Content Using Sensor and Weather Data

Cody Harris, harrcody@iu.edu, [fa20-523-305](https://github.com/cybertraining-dsc/fa20-523-305), [Edit](https://github.com/cybertraining-dsc/fa20-523-305/edit/master/project/project.md)

{{% pageinfo %}}

## Abstract

As the world is gripped with finding solutions to problems such as food and water shortages, the study of agriculture could improve where we stand with both of these problems. By integrating weather and sensor data, a model could be created to estimate soil moisture based on on weather data. While some farmers could afford to have many moisture sensors and monitor them, many would not have the funds or resources to keep track of the soil moisture long term. A solution would be to allow farmers to contract out a limited study of their land using sensors and then this model would be able to predict soil moistures from weather data.
 
Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** agriculture, soil moisture, IoT

## Background

Understanding how weather impacts soil moisture is something that has been studied in various ways, all because it is a driving factor in crop success. Multiple studies have sought to apply a deterministic approach to calculating soil moisture based on observational weather data. 

One such study, was motivated by trying to predict dust storms in China, in which soil moisture plays a large role in. This prediction used multiple-linear regression, and focused on predictions that dealt with the top 10 cm of soil. Two key takeaways can be derived from this work that are beneficial for carrying out this project.

- "The influence of precipitation on surface soil moisture content does not last more than 16 days."   
- "The compound effect of the ratio of precipitation to evaporation, which is nonlinearly summed, can be used to calculate the surface soil moisture content in China" [^4]. 

Moving forward, this project will assume that percipitation from the prior 16 days is relavent. In the case that for the specific data being fit, less days are relavent, then their coefficients in the model will likely become small enough to not effect the model. Secondly, soil moisture is influenced by a ratio or precipitation to evaporation. While this project might not seek to evaluate this relationship directly, it will seek to include data that would influence these ratios such as temperature and wind speeds.

Multiple publidcations have sought to come up with complete hydrological models to determine soil moisture from a variety of factors. These models are generally stochastic in nature, and are reliable predictors when many parameters of the model are avaliable. One such cited model requires a minimum or 19 variables or measured coeefficients [^5]. The authors of another study note the aformentioned study, as well as other similar studies, and make a point that these methods might not be the best models when it comes to practical applications. Their solution was to create a generalize model that relied mostly on soil moisture as "a function of the time-weighted average of previous cumulative rainfall over a period" [^6]. Such a model is closer in terms to simplicity and generalization to what is hoped to be accomplished in this project. 

The relationship between soil moisture and weather patterns is one with a rich history of study. Both of these measures effect each other in various ways. Most studies that sought to quantify this relationship were conducted at a time in which large scale sensor arrays could not have been implemented in a field. With the prevalance of IoT and improved sensing technologies, it seems as though there might not be a need to use predictive models for soil moisture, but instead just use sensor data. While this could be true in some applications, a wide array of challenges occur when trying to maintain these sensor arrays. Problems such as charging or replacing batteries, sensor and relay equipment not working if completely buried, but are in the way of farming if mounted above ground, sensors failing, etc. These were real challenges faced by the farm in which the soil moisture data was collected [^7]. The objective of this project is to create predictive models based on limited training data so that farmers would not need to deal with sensor arrays indefinitely.

## Topic Discussion

Maintaining correct soil moisture throughout the plant growing process can result in better yeilds, and less overall problems with the crop. Water deficiencies or surplus at various stages of growth have different effects, or even negligable effects[^1]. It is important to have an idea of how your land consumes and stores water, which could be very different based on the plants being used, and variation of elevation and geography.

For hundreds of years, farmers have done something similar to this model. The difference is the precision that we can gain by using real data. For the past few hundred years, farmers had to rely on mostly experience and touch to know the moisture of their soil. While many farmers were successful, in the sense that they produced crops, there were ways they could have better optimized their crops to produce better. The water avaliable to the plants is not the only variable that effects yeilds, but this project seeks to create an accessible model to which farmers can have predicted values of soil moisture without needing to buy and deploy expensive sensors.

The model created could be used in various ways. The first main use is to be able to monitor what is currently happening in the soil so that changes can be made to correct the issue if there is one. Secondly, a farmer could evaluate historical data and compare it to yeilds or other results of the harvest and use this analytical information to inform future descions.

This project specifically seeks to see the effect of weather on a particular piece of land in Washington state. This process could be done all over the world to obtain benchmarks. These benchmarks could be a cheap option for a farmer that does not have the funds to support a full study of water usage on their land. Instead, they could look for a model that has land that has similar soil and or geographical features, and then use their own weather data to estimate their soil moisture content.

## Datasets

The first data set comes from NOAA and contains daily summary data in regards to various measurments such as temperature, percipitation, wind speed, etc. For this project, only data that came from the closest station to the field will be used [^2]. In this case, that is the Pullman station at the Pullman-Moscow airport. Below is an image showing the weather data collection location, and the red pin is at the longitude and lattitude of one of the sensors in the field. This data is in csv format (see Figure 1).

![Figure 1](https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/images/distance_map.png)

**Figure 1:** Estimated distance from weather reports to the crop fields. Distance is calculated using Google Maps


The second dataset comes from the USDA. This dataset consits of "hourly and daily measurements of volumetric water content, soil temperature, and bulk electrical conductivity, collected at 42 monitoring locations and 5 depths (30, 60, 90, 120, and 150 cm)" at a farm in Washington state [^3]. Mainly, the daily temperature and water conent are the measurements of interest. There are multiple files that have data that corresponds to what plants are being grown in specific places, and the make up of the soil at each sensor cite. This auxilary information could be used in later models once the base model has been completed. This data is in tab delimited files.

Within the data, there are GIS file types that can be imported into Google Maps desktop to visualize the locations of the sensors and other geographical information. Below is an example of the sensor locations plotted on the sattelite image (see Figure 2).

![Figure 2](https://raw.githubusercontent.com/cybertraining-dsc/fa20-523-305/master/project/images/sensor_locations.png)

**Figure 2:** Location of sensors within the test field


## Data Cleaning and Aggregation

The first step is to get the soil moisture data into a combined format, currently it is in one file per sensor, and there are 42 sensors. See the data_cleaning_aggregation.ipynb file to see how this was done. After aggregation, some basic information can be checked about the data. For instance, there is quite a bit of NAs in the data. These NAs are just instances where there was no measurement on that day. There is about 45% NAs in the measurement columns. To further clean the data, any row that has only NAs for the measurements will be removed.

Next, the weather data needs some small adjustments. This is mostly in the form of removing columns that either are empty or have redundant data such as elevation. 

Once the data is sufficiently clean, some choices have to be made on joining the data. The simplist route would be to join the weather measurements directly with the same day the soil measurement, however, the previous days weather is likely to also have an impact on the moisture. In the same fashion, the weather for the 5 previous days might all have a large impact on the moisture. So simply joining the two data sets right now is likely not the correct course of action until further analysis is made.

## Pipeline for Preprocessing

Before feeding the data through a machine learning algorithm, the data needs to be manipulated in such a way that it is ready to be directly fed into an algorithm. This includes joining the two data sets, feature engineering, and other tasks that prepare the data. This will need to be done every time a new dataset is being used, so this must be built in a repeatable way. The machine learning library scikit-learn incoroporates something called "pipelines" that can allow processed to be sequentially done to a dataframe. For purposes of this project two pipelines will be built, one will be used for feature engineering and joining the data, the other will be used to handle preparation of numerical, categorical, and date data.

### Loading and Joining Data

This is the first step of the entire pipeline. This is where both the weather, and the soil moisture data are read in from csv files in their raw fromat. The soil moisture data is found in many different files, and these all need to be combined. After combining the fies, any lines that are full of NAs for the measurements are dropped. Next the weather data is loaded in. Both files have a date field which is the field they will be joined on. To make things consistent, both of these fields need to set be date format. 

When it comes to joining the data, each row should include the moisture content at various depths, as well as the weather information from the past ten days. While this creates a great deal of redundant data, the data is small enough that this is not an issue. Experiments will be done to evaluate just how many days of prior weather data are needed to form accurate results, while trying to minimize the number of the days.

### Feature Engineering

Currently only one feature is added, and this is a boolean flag that says whether it rained or not on a certain day. The thought behind this is, that for some days prior to the current measurement, the amount of rain might be needed, but for other days, such as 10 days prior, it might be more important to just know if there was rain or not. This feature is engineered within the pipeline. 

A future feature will be to use the months as categorical variables. While the date might be helpful, it probably is more accurate to consider the month then the specific day.

### Generic Pipeline

After doing operations that are specific to the current dataset, some built in processors from sk-learn are used to make sure the data can be used in a machine learning model. This means that for numerical data types, the pipeline will fill in missing values with 0 instead of leaving them as NaN. There might be experiements to decide how to deal with missing measurements. Also the various numerical fields must be standardized, this is important for models such as linear regression so one large variable isn't dominating the model.

As far as text and categorical features, the imputer will be used to fill in missing data as well. Then a process called one hot encoding will be used to handle the categorical variables so that they can be read into sk-learns estimators.

Lastly the date pipeline will take datetimes and convert them to integers that represent how many seconds it has been since 1970. This will allow dates to be handled as numerical values if they are used as an estimator instead of being used as a categorical feature as there would be many categories.

## Multiple Models for Multiple Soil Depths

There are a few different approaches for modeling for this particular problem. The issue is that we have multiple things we would like to predict with the same predictors. It is unlikely that the model that predicts for a depth of 30 cm, would accurately predict for a depth of 150 cm. In order to adjust the models, a seperate model will be created for each depth, with that said, the predictors are all the same for each depth, but the trained output is different. To accomplish this, five different datasets were constructed, each one representing a depth. All rows in which the predicted value is not avaliable for that depth were pruned from the dataset. 

## Splitting Data into Train and Test

In order to test any model created, there must be a split between test and training data. This is done by using a function in sk-learn. In this case, there are about 76k rows in the data set. For the training data, 80% of the total data will be used, or about 60.8k records. The split is done after shuffling the rows so that it does not just pick the top 80% everytime. Lastly the data is split using a stratified method. As we want to have models that take the specific area of the field into account, that means that we need to have the different areas of the field represented equally in both the training and testing dataset. This means that if 10% of the data came from sensor CAF0003, then roughly 10% of the training data will come from CAF0003 as well as 10% of the test data will be from this location.

## Preliminary Analysis and EDA

Before building a machine learning model, it is important to get a general idea of how the data looks, to see if any insights can be made right away.

The first two visualizations are grids that show the entire distribution of measurements across each sensor. The first grid is the volume of water at 30 cm, and the second grid is the water volume at 150 cm. Each chart could be looked at and examined on it's own, but what is most important to note is the variability of the measures from location to location. These different sensors are not that far away, but show that different areas of the farm do retain water in different ways. 

The third and fourth grid shows the temperature at 150 cm, the results are what would logically be expected. The different sensors do not show much variance from location to location.

A simple bar chart is used to get a quick overview of the percipitation values over the same time period to see the overall trends. The most interesting part of this analysis is from the end of 2009 to nearly 2012. There is very little percipitation in this time period. Which initially looks like an issue with the data, but when it is compared to the water volume charts, a correlation can be seen. It isn't perfect, but in many of the sensors that have data in this period, the moisture seems rather constant.

*Note*: After doing this analysis using the Altair library in python, the notebook became way too big due to the size of the data. As a quick remedy for this, I saved the visualizations as PNG and saved them in the images folder. They are named: one, two, three, and four, for the order that they are mentioned in the above section. I will remove the eda notebook from the repo.

## Initial Model Testing (Regressor)

Once the pipelines were setup, the first model could be tested for accuracy. As the output data is continuous in nature, the easiest machine learning algoritm to test to make sure everything is correct, was a linear regression model. It seems fairly likely that a linear regression model would do rather well with this data. The weather is the driving factor in soil moisture in a non-irrigated field, so this test is a litmus test to make sure that the data is good and provide a baseline measurment for future models. The experiment log below shows the returned values from the test that was run. Over the course of experimentation, a log such as this will be kept.

The results are as follows:

| Experiment | Depth | Fit_Time | Pred_Time | r2_score |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| First Linear Reg  | 30cm  | 58.701572 | 0.238179 | 0.890208 |
| First Linear Reg  | 60cm  | 58.847758 | 0.169551 | 0.898520 |
| First Linear Reg  | 90cm  | 54.927837 | 0.172255 | 0.882179 |
| First Linear Reg  | 120cm  | 64.877650 | 0.197685 | 0.884033 |
| First Linear Reg  | 150cm  | 63.256277 | 0.170247 | 0.876900 |

These results show that the data is pretty well correlated and that there is reason to believe that we could predict soil moisture from weather alone. Although an r^2 of around 0.87-0.89 are pretty good, with such highly related predictors, there is definitely room for model improvement. 

## Model Testing (Classifier)

While the output is continuous, there is an argument to use a categorical classifier model. For a specific plant, an optimal moisture range could be studied. For example sake, the range could be 0.2-0.4 units. Then it would not matter if the soil is 0.2 or 0.3, both would be in the acceptable range. With this in mind, certain levels could be created to alert the farmer of which category they could be experienecing. For example there might be five levels: too dry, acceptable dryness, optimal, acceptable wetness, and too wet. The training data could be adjusted to fit into these categories. 

Further experimentation will be required to decide if this is truly the best route for the model. This idea seems promising as predicting the exact moisture content is not as important as understanding the toleraable ranges. 

## Plan for the rest of the Semseter

The following is a plan for the rest of the semester, using the due dates for Assignments 8-11 as milestone dates

### November 16

- Tune Hyper-parameters
- Test various models
- Further tune and tweak models  
- Start analyzing various models and techniques to find the most accurate model
- Update report

## References

[^1]: O. Denmead and R. Shaw, "The Effects of Soil Moisture Stress at Different Stages of Growth on the Development and Yield of Corn 1", Agronomy Journal, vol. 52, no. 5, pp. 272-274, 1960. Available: 10.2134/agronj1960.00021962005200050010x.

[^2]: N. (NCEI), "Climate Data Online (CDO) - The National Climatic Data Center's (NCDC) Climate Data Online (CDO) provides free access to NCDC's archive of historical weather and climate data in addition to station history information. | National Climatic Data Center (NCDC)", Ncdc.noaa.gov, 2020. [Online]. Available: <https://www.ncdc.noaa.gov/cdo-web/>. [Accessed: 19- Oct- 2020].

[^3]: "Data from: A field-scale sensor network data set for monitoring and modeling the spatial and temporal variation of soil moisture in a dryland agricultural field", USDA: Ag Data Commons, 2020. [Online]. Available: <https://data.nal.usda.gov/dataset/data-field-scale-sensor-network-data-set-monitoring-and-modeling-spatial-and-temporal-variation-soil-moisture-dryland-agricultural-field>. [Accessed: 19- Oct- 2020].

[^4]: K. Shang, S. Wang, Y. Ma, Z. Zhou, J. Wang, H. Liu and Y. Wang, "A scheme for calculating soil moisture content by using routine weather data", Atmospheric Chemistry and Physics, vol. 7, no. 19, pp. 5197-5206, 2007 [Online]. Available: https://hal.archives-ouvertes.fr/hal-00302825/document

[^5]: W. Capehart and T. Carlson, "Estimating near-surface soil moisture availability using a meteorologically driven soil-water profile model", Journal of Hydrology, vol. 160, no. 1-4, pp. 1-20, 1994 [Online]. Available: https://d1wqtxts1xzle7.cloudfront.net/49029293/0022-1694_2894_2990031-020160922-30744-s4bk3h.pdf?1474528332=&response-content-disposition=inline%3B+filename%3DEstimating_near_surface_soil_moisture_av.pdf&Expires=1604966715&Signature=Q~p9g74lgChE6c7AfnE~Ep8179QUW~5HV0wpxotbyYtYONk-ns8Jku6oT9mTmKEw4wnix1Uol~zwOyxLObjdi8Cjg~LclJBo6CjFcxALrU1lpBnyzOML4hGOa9yiqEqwvrn3tG4tpsmysnOSznmj8kVTl2GGtMpblfyFl~x5QdwhcbVxvQrJDKRsdUsYOqfBeEiQahM7zgi8Gikrreh0AaLzM2GGpVcfXl8QD84XkbxdDJEinDAtWxW8yNKqrfNBnBqODCo9VusCXy-VJvJ9syFy5fTld~enjQfqHQtKyjszbXcNr1o~20uG78D8RlJyBnEECBh~M5miatLhhgig3Q__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA

[^6]: F. Pan, C. Peters-Lidard and M. Sale, "An analytical method for predicting surface soil moisture from rainfall observations", Water Resources Research, vol. 39, no. 11, 2003 [Online]. Available: https://agupubs.onlinelibrary.wiley.com/doi/pdf/10.1029/2003WR002142. [Accessed: 08- Nov- 2020]

[^7]: C. Gasch, D. Brown, C. Campbell, D. Cobos, E. Brooks, M. Chahal and M. Poggio, "A Field-Scale Sensor Network Data Set for Monitoring and Modeling the Spatial and Temporal Variation of Soil Water Content in a Dryland Agricultural Field", Water Resources Research, vol. 53, no. 12, pp. 10878-10887, 2017 [Online]. Available: https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2017WR021307. [Accessed: 08- Nov- 2020]
