a3-aljadaan-rlordon-olsufj
===============

## Team Members

1. Ahmad Aljadaan aljadaan@uw.edu
2. Ross Lordon rlordon@uw.edu
3. Jacob Olsufka olsufj@uw.edu

## Weather Condition For the USA in August 2013

# Introduction
For this assignment, our group decided to think of novel ways to visualize weather data. The reason why we chose this is because all of us have limited coding backgrounds and are all D3 novices. Our rationale was if we chose a data set with a small number of "moving parts" it would facilitate learning D3 more. We realize this visualization isn't the most novel or compelling, but we thought it would be a good first step towards learning interactive visualizations.

The initial plan was to allow the users to compare U.S. national weather data for 2013 and 2014 on two separate maps side by side. The user would be able to toggle between three main categories of data, which would be depicted on a choropleth map. The categories would be average daily temperature, max daily wind speed, and total daily precipitation. The user would also be able to mouse over each state to look up data for all the main toggle categories, plus additional information. Such as the maximum and minimum temperature, sunrise and sunset, or max wind speed direction. At the bottom of the display would be a brush allowing the user to toggle the data to a particular day.

![The initial visual display](http://i.imgur.com/oy6KrhN.jpg)

# Data Source and Transformation
Ross was the group member who spearheaded, obtained, cleaned, and consolidated the data into a usable format. At the suggestion of a colleague earning his PhD in Atmospheric Science at the University of Utah, we obtained our data from the [National Oceanic and Atmospheric Administration's (NOAA) National Centers for Environmental Information (NCEI).](https://www.ncdc.noaa.gov/) Once we started interacting with the system, we quickly realized the scope of our project was very large in regards to the complexity of downloading the data. The interface is extremely old. Users must drill down to each individual weather station by month. There is also substantial latency time interacting with query system. Some queries took up to 5 minutes to complete, which only yielded one months worth of data in one state. In light of this, the project was quickly scoped down to just the month of August for both 2013 and 2014 to ensure we didn't spend too much time getting out data. 

The weather station for each state was selected based on the [highest amount of ridership for each airport in each state](https://en.wikipedia.org/wiki/List_of_airports_in_the_United_States). The reason is, most professional meteorologists based their reporting on weather data at the airport. Furthermore, the weather stations at major airports are more robust and more reliable because so many commercial pilots are dependent on this data. This does lead to some bias in regards to bigger states such as Alaska, California, or Texas. One weather station is not representative of the entire state but to keep things simple for the project, we narrowed the scope of data sources using these parameters. There was also one exception to the rule regarding the airport needing to be the busiest. In Wyoming the busiest airport is in the ski town Jacksonhole. However, the weather station is exceptionally unreliable, and for both years in August more than half the data was reported as "missing". In light of this, the airport in the capitol city of Cheyenne was selected instead. 

In order to get the data into a usable format, each weather station had to be queried for August of 2013 and 2014. The data was then presented inside the web browser as csv text. This had to be copied and pasted into an excel file because no download option is available. Once this was done, each individual month's data set was cleaned up using a variety of custom built Excel Macros. This allowed us to get the data into a usable format before combining into a cohesive data set. Once the data was combined, the [Federal Information Processing Standard state codes](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standard_state_code) were manually added in order allow processing by the D3 geomap. Overall Ross spent approximately 10 hours to get the data into a usable format. 
