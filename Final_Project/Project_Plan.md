# How Big Data Technologies Can Improve Indoor Agriculture

## Team
Cody Harris
harrcody@iu.edu

## Topic Discussion
The overall topic of the project will include investigating how a host of Big Data technologies could be leveraged to improve multiple facets of the growing and distribution process for indoor farmers. One of the biggest benefits of growing indoors is the ability to precisely control the growing environment. From the light intensity and spectrum, to the nutrients given to the plant, there is an optimal combination of variables that produce the best results. Each farmer has priorities, whether those are yield, produce quality or a combination of various factors, it is a complex system that requires experimentation and robust tools to see the best results. There are a host of IoT sensors and controllers that can be employed to help monitor and control the growing environment, these all produce vast amounts of data that must be sifted through to extract insights. For sizeable farms, this produces big data problems that must be overcome. 

While some insights from the data can come during or directly after the growing “season”, some requires the produce to hit the shelves or to be used to create various food products. This means monitoring continues through the logistics process, and this data is integral when it comes to the end result of the produce. All this data allows for traceability in the food supply chain as well, in which big data technologies are perfect to handle. 

The end goal is to investigate and implement a scalable solution that follows the farmers crops from seed to consumers tables and optimizes the process along the way. Although indoor farms allow for great control, it is important to understand that there are many costs that are not associated with traditional farms. This means that to make the farming endeavor sustainable, optimization is important.

## Dataset
There are not any publicly available data sources that meet the needs of this project. In order to accomplish the goal of building an analytics platform for an indoor farm and the related logistics, simulation data will be created. The simulation data will encompass many different situations that could be encountered and labeled by these issues. Along with possible issues, the data will include mostly satisfactory situations, as this is what the farmer is most likely to encounter.

The majority of the data being worked with will be streaming sensor data. The sensors will include: PAR (Photosynthetically Active Radiation), temperature, humidity, pH of grow medium, and CO2. Along with these streaming measurements, other data points about the specific grow area will be taken. A grow area could be as small as a row of ten plants, all the way to thousands of plants. These datapoints could be things such as phenotype, light spectrum, light cycle, feeding schedule, or any other labels that could be beneficial in determining the end attributes of the given produce. 

Variance in the data will come in a variety of forms. As completely identical data is not analogous to real life, it can be for certain measurements. For example, in an indoor growing environment equipped with HVAC, the temperature might only fluctuate a few percent all day, and then have a rapid change as the lights are turned off. With this in mind, certain simulation measurements should not have a great deal of noise in them unless trying to simulate an adverse event.

As this data is streaming, the dataset will be a time series that needs to be handled in the sense of streaming as well as in a postmortem capacity. The size of the data should be large enough to properly simulate a large farm over the course of a grow cycle. 




