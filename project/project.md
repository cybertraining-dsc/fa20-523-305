# Estimating Soil Moisture Content Using Sensor and Weather Data

## Team
Cody Harris
harrcody@iu.edu
=======
Cody Harris, harrcody@iu.edu, fa20-523-305

{{% pageinfo %}}

## Abstract

As the world is gripped with finding solutions to problems such as food and water shortages, the study of agriculture could improve where we stand with both of these problems. By integrating weather and sensor data, a model could be created to estimate soil moisture based on on weather data. While some farmers could afford to have many moisture sensors and monitor them, many would not have the funds or resources to keep track of the soil moisture long term. A solution would be to allow farmers to contract out a limited study of their land using sensors and then this model would be able to predict soil moistures from weather. 

Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** agriculture

## Topic Discussion

Maintaining correct soil moisture throughout the plant growing process can result in better yeilds, and less overall problems with the crop. 

## Dataset
There are not any publicly available data sources that meet the needs of this project. In order to accomplish the goal of building an analytics platform for an indoor farm and the related logistics, simulation data will be created. The simulation data will encompass many different situations that could be encountered and labeled by these issues. Along with possible issues, the data will include mostly satisfactory situations, as this is what the farmer is most likely to encounter.

The majority of the data being worked with will be streaming sensor data. The sensors will include: PAR (Photosynthetically Active Radiation), temperature, humidity, pH of grow medium, and CO2. Along with these streaming measurements, other data points about the specific grow area will be taken. A grow area could be as small as a row of ten plants, all the way to thousands of plants. These datapoints could be things such as phenotype, light spectrum, light cycle, feeding schedule, or any other labels that could be beneficial in determining the end attributes of the given produce. 

Variance in the data will come in a variety of forms. As completely identical data is not analogous to real life, it can be for certain measurements. For example, in an indoor growing environment equipped with HVAC, the temperature might only fluctuate a few percent all day, and then have a rapid change as the lights are turned off. With this in mind, certain simulation measurements should not have a great deal of noise in them unless trying to simulate an adverse event.

As this data is streaming, the dataset will be a time series that needs to be handled in the sense of streaming as well as in a postmortem capacity. The size of the data should be large enough to properly simulate a large farm over the course of a grow cycle. This data set will simulate an experiment, in which a variety of conditions or phenotypes will be compared to a control. Within the realm of the experiment the simulation data might include adverse events, such as a power outage, that could actually occur during an experiment and these adverse events must be accounted for in the end conclusion. 

## Getting a Good Grade
As I am a graduate student, I am expected to not only write a report, but also create a software component. For the software, it will be a proof of concept to show that a scalable solution could be built to use open source big data technologies. The report will detail the work done in the solution being built, as well as exploring ideas that cannot be built but are required for the full solution to be implemented. 

### Data Storage and Streaming
With a focus on open source platforms, Apache has solutions that can be leveraged to handle many aspects of big data streaming and storage in a distributed computing environment. While more investigation needs to be done on the exact software that will be used, Hadoop, Spark, or the combination of the two will be used to handle the large amount of data, whether that is for longer term storage or real time streaming. Another Apache system that will be evaluated is Kafka, but again, there are many possibly solutions to be used. The goal is to stay within the Apache environment as it is widely used in industry as well as is an open source platform.

### Analytics
The analytics component of this project is diverse. While all goals might not be able to be achieved in the proof of work, all of the data needs that are required for the growing and logistics processes of an indoor farm will be evaluated and explained in the final report. There are two main components to the analytics: real time analytics and historic data analysis. While some models are being fine tuned for the specific farm, the real time analytics will likely be mostly monitoring at the beginning. As grow seasons go by and metrics are collected on the harvest, the real time analytics will be informed by the historic data using some sort of machine learning processes. These analytic goals can likely be completed using tools within Spark, using MLlib. If this cannot be accomplished, then another library will be used such as sci-kit learn. 

### Hardware
It is important that the proof of concept is designed for a distributed computing environment. The goal is to create open source software that can be used by small farms that sell solely at farmers markets, all the way to large commercial operations. When designing in this way, growing pains in the future can be minimized. For the hardware being used, multiple solutions are being evaluated. The first possible idea is using a commercial cloud application such as AWS, Azure, Google Cloud, etc. Secondly, personal local hardware could be used to create a virtual distributed computing environment. There are two options for local hardware. Either a personal computer with multiple virtual machines, or an array of Raspberry Pi’s will be used. 

### Novel Ideas
Everything that has already been explained has more or less been attempted or implemented successfully. The innovation comes by trying to implement some ideas that are fresh by borrowing ideas and implementing them in the context of an indoor produce farm. The first big deviation from the norm is using a blockchain backbone to store immutable data. This idea is used in some niche farming scenarios but is yet to be adopted by produce farmers. Blockchain could be used to hold the logistical data to establish immutable custody data, but also to store the data from the growing process, pesticides tests, chemical makeup tests, genetic markers and more. Next, in the spirit of providing transparency there will be a public blockchain that could be explored by consumers or businesses that buy the farmers produce. In today’s world, we always wonder if we are paying some premium for products in order to just have a special label on that product. For this example, the label is: organic, GMO free, pesticide free, etc. Transparency goes a long way to prove to consumers that you are doing more for them to provide a good product, which allows for a greater amount that people are willing to spend. Some data might be proprietary, such as the exact genome of the phenotypes being used, or the specific growing protocols, so this information must stay off the blockchain.

### Extensions
Not everything can be built or examined completely within the time constraints. Part of the project will be planning future updates or technologies that could improve the solution. One immediate future plan would be to incorporate cameras and computer vision to monitor the crops. Using images of plants, certain diseases, pests, or nutrient deficiencies can be seen as soon as they start to develop, giving the farmer the best odds at reversing the issue without effecting the harvest. Many of these issues cannot be greatly noticed with sensor data alone, which requires a farmer to constantly visually inspect crops. While this might not be terribly hard in some cases, some vertical grows might require large ladders to see all levels of the crop. This improvement could lead to less staff being required, which can allow more farmers to grow more for less money. 
