# reservoirtimeseries

![Folsom near its lowest all-time level during the catastrophic 2012-2015 drought](images/FolsomMain.jpeg?raw=true)

# Introduction

The goal of my project was to investigate how machine learning could assist in reservoir prediction in California. California has one of the most complex water management systems in the world; however, it teeters on the edge of crisis given the increasingly destabilized climate conditions it faces. Rain seasons have become more varied, the annual snow pack and its key spring melt have shrunk, and droughts have increased in duration and intensity. I believe data science could play a key role in using California's water resources wisely.

Within the past two decades, data science has made many breakthroughs in water level prediction across the world. That being said, California's long-term prediction systems are still hard-inputted from water data halfway through the rain year. I wanted to see if there was potential in long-term system prediction storage. (That being said one standout of California's water engineering is its use of machine learning for short-term flood control predictions- crucial for preventing events like the Oroville Dam failing in 2017 from heavy rains)

As incorporating exogenous variables quickly proved to be weaker than a seasonal, auto-regressive endogenous model, once the data was adjusted it became a clear mater of a grid search to find the best SARIMA model.

#Research Resources

As stated above, there has been extensive research on time series and water systems. While not usually focused on reservoirs,v these papers were still incredibly conducive starting points to visualizing my project.

First off, 'Development of Water Level Prediction Models Using Machine Learning in Wetlands: A Case Study of Upo Wetland in South Korea' by academics in Korea and America was incredibly helpful in determining approaches to compare model success on test sets. They use multiple time periods for test sets, allowing to see model accuracy in both normal and extreme conditions. 

Additionally, to understand the current state of research into California's reservoirs, I utilized a lot of information from the University of California's environmental programs. 'Drought and the Sacramento–San Joaquin Delta, 2012–2016: Environmental Review and Lessons' was one of the more helpful papers I read.


#Data Reproduceability

We pull from two different online data query sources sources: one for reservoir-specific data and one for precipitation data. Water years instead of calendar years are used as precipitation totals and seasonality are best reflected. So each year runs from the beginning of October to the end of the following September.
We are using the 1990 water year onwards until the end of the 2021 season , so each pull is from October 1st 1989 until September 30th, 2020.

The reservoir data can all be pulled from the US Bureau of Reclamation's Reclamation Information Sharing Environment:
https://data.usbr.gov/catalog/

You search the name of the lake in question, then you can pull specific data. Storage data is labeled as 'Storage-af Time Series Data'. Evaporation data,
which we use to model temperature, is labeled 'Evaporation-cfs Time Series', the mean cubic feet per second of evaporation each day. I only used evaporation data for Folsom Lake as I determined that exogenous variables weren't useful. The lakes data I queried and used were:
-New Melones
-Trinity
-Shasta
-Don Pedro
-Exchequer
-Pine Flat
-Millerton
-Berryasa
-Oroville


Meanwhile, the precipitation data is also easier queried but exists in an outdated format. The California Data Exchange Center's website has a water year query section at thelink below. I typed in each index, 5SI for the Southern Sierra Index - San Joaquin Watershed, and 8SI for the . I used monthly data as I aggregrated up into 12 seasonal periods to make the data digestible for modelling; however, daily is also available in the drop-down menu.

