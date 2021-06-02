## Pandas EDA Case Study 1
-------------------------------------
# The Right Stops: Data-driven Location scouting for the Train-loving Influencer

### please add your names or github names here
* emichaelbernardo@gmail.com 
* murphykimberlyann@gmail.com 

-------------------------
## Background
InfluenzYa is an influencer marketing agency that supplies end to end social media analytics, brand development and logistics support for content creators and producers.  

They were recently approached by Jack Morris, a travel content creator with over 2.5 million followers.  As an influencer, he wants to bring the old world appeal of old train stations to his audience. To do this he wants to travel and photograph the stations across the world with the oldest (pre-1900) train stations. To optimize his travel budget and maximize his opportunities to create shareable images, he has tasked InfluenzYa to supply him with possible destinations.
![alt text](images/JACKMORRIS.png)
![alt text](images/OldStationsGram.png)

----------------------
## Objectives
* Provide a list of cities that have the oldest (pre-1900) train stations  still in operation. Show these on a world map
* Provide a list of possible destinations to create images for social media content
    * Show these stations on a map
    * List top oldest stations per city
* Recommend possible story telling angles to pursue to create engaging content
    * Data-driven imagery/art for Instagram
    * Sharable charts for social media
    * Historical or socio-economic insights 

## The Data 
Data was pulled from the following data sources:
* stations.csv
* cities.csv
* tracks.csv
* track_lines.csv
* station_lines.csv
* systems.csv
* lines.csv
---------------------------
Each of the data sources were brought into dataframes and cleansed. Our results excluded data that had:
* NaN and negative values for builddate, opening, closure.
* Missing values for the station name
* Duplicate rows that refered to the same station names wherein we used the first occurence of the station name as the basis to pull other columns.

* <b>note: </b> The cleaning process removed a significant amount of data from the source material; there are 3578 entries returned for a simple query of 'stations.csv' to find stations with an opening date prior to 1900. Our cleaned dataframe 'old_stations', which only contains stations built prior to 1900, contains 935 records for the entire world.
------------------------


In order to create the required charts and visualizations, we created our main dataframe (old_stations) which focused on the fields:

* **opening, builddate and closure** which allowed us to determing if a station was still in operation, as well as filter which stations which were opened between 1800-1900. These fields contain numerical data; specifically for 'closure', a value of 999999.0 indicates the station is still in operation.

* **id** was commonly used across several dataframes, which we used to merge with other tables to display actual station names as well as the cities and countries that they are located in. Though this field is numerical, it is the key to connecting the text data for city names ('name' in cities.csv) and station names.

* **geometry** was split up and used to create lattitude and longitude pairs to plot where stations are located on the the maps.

--------------
## Visualizations and Charts 
<!--
<figure class="image">
  <img src="images/heatmglobal.png" alt="fig. 1 Heat Map of pre-1900 Stations">
  <figcaption>fig. 1. Heat Map of pre-1900 Stations</figcaption>
</figure>
//-->
Map           |  Description
| :-------------------------:|:-------------------------: |
| <img src="charts/oldtable.png" width="700" >  | This is an excerpt of the initial list created by merging the  stations data with the city data and indexing by country, and city |
|<img src="charts/OldestStationsByCity.jpg" width="700" > | After removing entries with no build date, station name, opening data, we plotted the number of open stations against city names.|
|  |  |
|<img src="images/HeatGlobe.png" width="700" >| It is easier to see this data on a heat map. This better illustrates the distribution of pre-1900 stations across the globe. Notice that stations are clustered around 5 distinct areas.|
|  |  |
|<img src="images/HeatNY.png" width="700" > | Let's zoom into the cluster with the most red. In this case, red means there are more stations that fit our criteria |
|  |  |
<<<<<<< HEAD

more stuff | and then more stuff

### Oldest Train Stations in the World
(Kim please give a brief bit about the maps you plotted)

[Boston](https://cdafound.info/tst/Boston.html)

[Buenos Aires](https://cdafound.info/tst/Buenos%20Aires.html)

[chicago](https://cdafound.info/tst/chicago.html)

[Edinburgh](https://cdafound.info/tst/Edinburgh.html)

[Glasgow](https://cdafound.info/tst/Glasgow.html)

[London](https://cdafound.info/tst/London.html)

[Melbourne](https://cdafound.info/tst/Melbourne.html)

[Milan](https://cdafound.info/tst/Milan.html)

[New York](https://cdafound.info/tst/New%20York.html)

[Osaka](https://cdafound.info/tst/Osaka.html)

[Sao Paulo](https://cdafound.info/tst/S%C3%A3o%20Paulo.html)

[Santiago](https://cdafound.info/tst/Santiago.html)

[Sydney](https://cdafound.info/tst/Sydney.html)

[Tokyo](https://cdafound.info/tst/Tokyo.html)

[Valpariso](https://cdafound.info/tst/Valpara%C3%ADso.html)



=======
| <img src="images/NYZoom1.png" > We can look at the same data using a more detailed map.| <img src="images/NYzoom2.png" > We can zoom in further to reveal the actual station locations as you would see them on map apps on your phone or browser|
<!--[Stations around the World](charts/countrywisestations.png)//-->
![Stations around the World](charts/globaldistribution.jpg)
 In this chart above, we expanded the search parameters to show pre-1940 stations. This would cover what is refered to as the "First Era of Industrialization". Cities like London, New York and Chicago hosted "World Expositions" to show off new technological advancements. 

<b>Note:</b> In some cases like in Japan, Italy and the United States, new stations were errected across different cities for others most train hubs are centralized in a single city. 

-----------------
<table> 
<thead> Here are the top 10 Oldest Stations in Each city</thead>
 <tr>
 <td><img src="charts/Osaka_stationsV2.png" > </td>
 <td> <img src="charts/London_stationsV2.png" > </td>
 <td> <img src="charts/Chicago_stationsV2.png" > </td>
 </tr>

 <tr>
 <td><img src="charts/Buenos_Aires_stationsV2.png" > </td>
 <td><img src="charts/Valparaíso_stationsV2.png" width="200"> </td>
 <td><img src="charts/Sydney_stationsV2.png" > </td>

 <tr>
 <td><img src="charts/Boston_stationsV2.png" > </td>
 <td><img src="charts/Edinburgh_stationsV2.png" width="200"> </td>
 <td><img src="charts/Glasgow_stationsV2.png" > </td>
 </tr>

 <tr>
 <td><img src="charts/Melbourne_stationsV2.png" > </td>
 <td><img src="charts/Milan_stationsV2.png" width="200"> </td>
 <td><img src="charts/New_York_stationsV2.png" > </td>
 </tr>

  <tr>
 <td><img src="charts/Sao_Paulo_stationsV2.png" > </td>
 <td><img src="charts/Tokyo_stationsV2.png" width="200"> </td>
 <td>
 </td>
 </tr>
 
 </table>
<b>Note:</b> If you look closely at the charts above you will notice that in some cities like Chicago and Tokyo, they reflect a surge in construction. Chicago in particular coincides with preparation for the World's Fair.
<br>
----------------------------------
# <h2><b>View From Above</b></h2>
Plotting the location of every station can give us a better view of what the tracks look like. 
<table>
 <tr>
 <td align="center"><img align="center" src="charts/Chicago_lines.png" width="300" height="300"> Chicago</td>
 <td align="center"><img align="center" src="charts/NewYork_lines.png" width="300" height="300"> New York</td>
 </tr>
 <tr>
 <td align="center"> <img align="center" src="charts/Osaka_lines.png" width="300" height="300"> Osaka</td>
 <td align="center"><img align="center" src="charts/Tokyo_lines.png" width="300" height="300"> Tokyo</td>
 </tr> 
 </table>


## Insights 
-----------------
### Oldest Operational Train Stations in the World
![Oldest train stations still open](charts/oldest_stations_still_open.png)

-----------------
>>>>>>> d89bfa4e823fd672e08925de18c64719679684d4
### Top Cities with the most pre-1900 operational train stations 

insert relevant images here
(Rohan please give a brief bit about the chart you plotted)

--------------
### Why are these old stations relevant?

They served as a centroid for many socio-cultural and economic advancements. 
Rail Stations were the hub of transportation, commerce and culture (worlds fair, making global goods more accessible in land, etc)

insert relevant images here

-----------------
## Conclusion 
Here are what we believe are the best destinations that the client can consider to maximize opportunities to create content centered on pre-1900 train stations.
| Country | City     | Map | Tracks | Site | 
| ---     | ---      | --- | ---    | ---  |
| USA     | New York | [Map](https://cdafound.info/tst/New%20York.html) | [Track](charts/NewYork_lines.png) | [MTA](https://new.mta.info/) |  
|         | Chicago| [Map](https://cdafound.info/tst/chicago.html) | [Track](charts/Chicago_lines.png) | [CTA](https://www.transitchicago.com/) |  
| United Kingdom | London | [Map](https://cdafound.info/tst/London.html)| [Track](charts/London_lines.png) | [London Rails](https://www.nationalrail.co.uk/) | 
| Japan   | Tokyo | [Map](https://cdafound.info/tst/Tokyo.html)| [Track](charts/Tokyo_lines.png) | [Tokyo Metro](https://www.tokyometro.jp/en/) | 
|         | Osaka | [map](https://cdafound.info/tst/Osaka.html) |  [Track](charts/Osaka_lines.png)| [Osaka Transit](https://osaka-info.jp/en/page/kansai-route-network)| 

-----------------

## Future Improvements
Further exploration of the data could lead us to a better understanding of how the development of the rail system occured over time. Knowing when these systems grew the most, would allow us to investigate how they tied into the industrial revolution and the how it led to developement of the our current transportation system. This would also allow the client to create more informative and interesting content.

Joining this data with data pertaining to the development of the actual trains coupled with data regarding the architecture of these stations would also be a great angle to pursue from historical, engineering and aesthetic perspectives.

------------

## Additional Information
[Rail Transit History](http://www.trainhistory.net/railway-history/railroad-history/)

Interactive maps:

[Boston](https://cdafound.info/tst/Boston.html)

[Buenos Aires](https://cdafound.info/tst/Buenos%20Aires.html)

[chicago](https://cdafound.info/tst/chicago.html)

[Edinburgh](https://cdafound.info/tst/Edinburgh.html)

[Glasgow](https://cdafound.info/tst/Glasgow.html)

[London](https://cdafound.info/tst/London.html)

[Melbourne](https://cdafound.info/tst/Melbourne.html)

[Milan](https://cdafound.info/tst/Milan.html)

[New York](https://cdafound.info/tst/New%20York.html)

[Osaka](https://cdafound.info/tst/Osaka.html)

[Sao Paulo](https://cdafound.info/tst/S%C3%A3o%20Paulo.html)

[Santiago](https://cdafound.info/tst/Santiago.html)

[Sydney](https://cdafound.info/tst/Sydney.html)

[Tokyo](https://cdafound.info/tst/Tokyo.html)

[Valpariso](https://cdafound.info/tst/Valpara%C3%ADso.html)
