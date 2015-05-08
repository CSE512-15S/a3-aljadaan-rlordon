a3-aljadaan-rlordon-olsufj
===============

## Team Members

1. Ahmad Aljadaan aljadaan@uw.edu
2. Ross Lordon rlordon@uw.edu
3. Jacob Olsufka olsufj@uw.edu

## Weather Conditions in the USA for August, 2013
In this project we wanted to see how different weather attributes changes among the states. There are a lot of weather attributes provided to us from the National Oceanic and Atmospheric Administration's (NOAA) National Centers for Environmental Information (NCEI). We limited our scope to Average Temperature, Average Wind Speed, and Total Precipitation. We have produced an interactive visualization that allow users to chooses the weather attribute they want to visualize and scroll over the day of the month.

##Running Instruction

Access our visualization at [this link](http://cse512-15s.github.io/a3-aljadaan-rlordon-olsufj/index.html) or download this repository and run `python -m SimpleHTTPServer 9000` and access this from http://localhost:9000/.

## Introduction
For this assignment, our group decided to think of novel ways to visualize weather data. The reason why we chose this is because all of us have limited coding backgrounds and are all D3 novices. Our rationale was if we chose a data set with a small number of "moving parts" it would facilitate learning D3 more. We realize this visualization isn't the most novel or compelling, but we thought it would be a good first step towards learning interactive visualizations.

The initial plan was to allow the users to compare U.S. national weather data for 2013 and 2014 on two separate maps side by side. The user would be able to toggle between three main categories of data, which would be depicted on a choropleth map. The categories would be average daily temperature, max daily wind speed, and total daily precipitation. The user would also be able to mouse over each state to look up data for all the main toggle categories, plus additional information. Such as the maximum and minimum temperature, sunrise and sunset, or max wind speed direction. At the bottom of the display would be a brush allowing the user to toggle the data to a particular day.

![The initial visual display](http://i.imgur.com/oy6KrhN.jpg)

## Data Source and Data Cleaning
Ross was the group member who spearheaded, obtained, cleaned, and consolidated the data into a usable format. At the suggestion of a colleague earning his PhD in Atmospheric Science at the University of Utah, we obtained our data from the [National Oceanic and Atmospheric Administration's (NOAA) National Centers for Environmental Information (NCEI).](https://www.ncdc.noaa.gov/) Once we started interacting with the system, we quickly realized the scope of our project was very large in regards to the complexity of downloading the data. The interface is extremely old. Users must drill down to each individual weather station by month. There is also substantial latency time interacting with query system. Some queries took up to 5 minutes to complete, which only yielded one months worth of data in one state. In light of this, the project was quickly scoped down to just the month of August for both 2013 and 2014 to ensure we didn't spend too much time getting out data. 

The weather station for each state was selected based on the [highest amount of ridership for each airport in each state](https://en.wikipedia.org/wiki/List_of_airports_in_the_United_States). The reason is, most professional meteorologists based their reporting on weather data at the airport. Furthermore, the weather stations at major airports are more robust and more reliable because so many commercial pilots are dependent on this data. This does lead to some bias in regards to bigger states such as Alaska, California, or Texas. One weather station is not representative of the entire state but to keep things simple for the project, we narrowed the scope of data sources using these parameters. There was also one exception to the rule regarding the airport needing to be the busiest. In Wyoming the busiest airport is in the ski town Jacksonhole. However, the weather station is exceptionally unreliable, and for both years in August more than half the data was reported as "missing". In light of this, the airport in the capitol city of Cheyenne was selected instead. 

In order to get the data into a usable format, each weather station had to be queried for August of 2013 and 2014. The data was then presented inside the web browser as csv text. This had to be copied and pasted into an excel file because no download option is available. Once this was done, each individual month's data set was cleaned up using a variety of custom built Excel Macros. This allowed us to get the data into a usable format before combining into a cohesive data set. Once the data was combined, the [Federal Information Processing Standard state codes](https://en.wikipedia.org/wiki/Federal_Information_Processing_Standard_state_code) were manually added in order allow processing by the D3 geomap. Overall Ross spent approximately 10 hours to get the data into a usable format. 

## Data Exploration
Ahmad was working on exploring the data using different tools such as (Tableau and ggplot). We wanted to start with a simple question to know the data set. A simple question will allow us to detect if there is some data missing or not defined properly. For example, in R we had to change some variables into numeric. Also, the data file assigned T as a variable in the Total Precipitation column which is somewhere between 0.01 and 0.02 inches of rain. In our first data exploration in Tableau we noticed a missing data for the State of Kansas. Sometime with large data set, where we have daily data points for each state for the whole year, it can be cumbersome to detect missing data manually. (see below)

![The initial visual display](http://i.imgur.com/4XGgBM0.png?1)

As we fixed the data our vehicle moved on to its exploration journey. Tableau is a great tool for data exploration, with it we where able to ask questions such "Hottest State in August?" and "States with highest total of precipitation?". We started with the use of mapping function in Tableau. We were able to comapre data set from both 2013 and 2014.

![The initial visual display] (http://i.imgur.com/EUqt3KT.jpg?1)
![The initial visual display] (http://i.imgur.com/2SeFTbv.jpg)

Moreover, as we went through the data and looking from the graph created above new questions emerged. We wanted to know the spacious relationship of the total precipitation among states in 2013 and 2014. For that, we used packed bubbles as a visualization method. In this visualization, we can see the huge drop in Alaska precipitation from 21 inches in 2013 to 13 inches in 2014. Also, we can notice that most states are getting more rain in 2014 with the increase size of the bubbles. In addition, we can notice that the Midwest states are getting more rain in 2014 compared 2013. 

![The initial visual display] (http://i.imgur.com/54GNhvy.jpg)

Some prelimiary work have been done with R where we tried to explore more stuff with the possibility to build interactive maps with ggplot and Shiny packages. It was a learning experience but we ran into data problems since R require a different data cleaning than excel. A major error we ran into when using ggplot is "Discrete Value supplied to continuos scale". Although, we where able to plot a static map using ggplot (see below), we couldn't implement Shiny library to create an interactive map. 

![The initial visual display] (http://i.imgur.com/OpR7F61.png)

Overall, Ahmad spent a total of 18 hours, most where in getting ggplot and Shiny to work. In addition, he tried to build another d3 interactive visualization where he failed to produce the map due to some problems in his code (The legend was working though!).

## Final Visualization
Jacob was responsible for the implementation of the interactive design. D3 was the tool of choice, one of the main reasons why we all took this class was to begin to learn D3 so this assignment gave us great hands on experience learning it, and that was the main takeaway from A3 that we most excited about. Jacob had been creating choropleth maps from scratch using processing, so he was very interested in how to make these same types of visualizations using D3.
He found some nice tutorials online on creating choropleth maps using D3, and he chose to use an existing package called geomap that included all of the topojson files for the paths of the outlines of the states, and includes color schemes taken from the color brewer project. The slider was implemented using a d3-slider package that was found on github, with some custom CSS and design added. Also, he included dots for the location of each airport, along with a custom mouse over tooltip that displays the respective airport name. 
Our project uses red and green as two of the color schemes. The reason why we do not believe this is a problem as far as red/green color blindness goes is the two colors are never displayed on the map at the same time. Additionally, the colors indicate what variable we are looking at (temperature, wind or precipitation), but that information is redundantly displayed with a title, so we deemed it a non-issue.

Below are two stages for the visualization:

Before:
![The initial visual display] (http://i.imgur.com/PXvDX4R.png)

After:
![The initial visual display] (http://i.imgur.com/aSPhpNu.png)

Jacob spent 25+ man hours spent implementing this project. Much of those hours were fighting through learning, debugging, and gaining a general understand of how D3 works, as he still in the beginner stages of his web development skills. 

##Lessons
If we were to start this project over from scratch we would not choose to use the geomap package. It is a nice starter package for creating a choropleth map that includes automatic legend drawing and coloring schemes, but limits customization of the features. A few known bugs exist in the interactive vis, because of this use of the geomap package. The first bug is that the package thinks that Minnesota is Nevada, and so the color encoding and tooltip all display Minnesota as Nevada. We know that it is a package issue and not because of error in our data, or our code because on the geomap.js website the example that they have has this bug as well. Another problem, and one that makes the interaction not as beautiful or useful as it should be, is that every time you change the day on the slider a new <svg> is created to display the resulting map so there is this annoying flashing effect. When you drag the slider this flashing takes away from the ability to perceive changes in the map. In the geomap package, you call the map to be drawn through a map.draw command, and digging into the geomap.js we discovered that every time the draw command is called it appends a new svg to the DOM. Clearly this package was not created to be redrawn in an interactive way like we are doing, and if we would have realized this earlier we would have been able to switch our efforts to a new strategy. We were unable to implement the two different maps for each year strategy that we had initially intended for, again because the geomap implementation did not allow for this. A final bug is that when you click on portion of the map to zoom, the airport dots do not zoom with them. All in all, the next step for us in our learning process will be to create something like this without the help of geomap (coding from scratch).

##Limitations
One limitation of our visualization is that since geomap auto creates the color bins based on the input data’s max and min, color comparisons between days are not necessarily entirely accurate. For each day however, the color comparisons between states are still useful. There is much more in terms of displaying data that could be done to further the comparisons, such as including other types of charts to the side to accompany the choropleth map, but for the scope of our skill set we settled on just some basic interactions. 
 
## Changes between Storyboard and the Final Implementation
From our development process it can be seen that we haven't diverted a lot from the storyboard original idea. The diversion occurred due to our novel expertise in d3 and JavaScript. Our skill set limited us from pursing the original goal. We originally wanted to compare weather attributes in two maps where each map represents a year (2013 Vs. 2014). We end up showing only one map due to some errors that we kept having.  Looking at our first sketch (see top of the page) with the map, the three buttons (Temperature, Wind, and Perception), the day scroll bar, and mouse over description box; it looks exactly the same to our final visualization.    
