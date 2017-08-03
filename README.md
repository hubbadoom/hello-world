### Runway orientation verification

#### Introduction

The following will allow the operator to check any airport runway orientation around the world within the limitations of the data available
from FlightRadar24 on Foundry.
This process answers initially to some detected inconsistencies in certain runway orientation data in the scope of the new Head Unit Display
developped by Airbus. They need a precision of 0.3 degrees to proceed the landing or the take-off of the plane. This study comes therefore
to support other means of runway orientation data validation.

All the calculation are based on the FlightRadar24 positions dataset available in Foundry. See extract below :

![FR24_positions](https://rosewood.palantircloud.com/blobster/api/salt/ri.blobster.main.image.7e3c9e01-9b23-437b-87ad-2b7d5d7e3676)

The initial dataset available in Foundry was filtered to contain positions of aircraft landing and taking off coming from trustworthy sources.

Two methods were developped, one based on the heading values displayed by the dataset and another one based on the positions (longitude and latitude) 
also displayed in the dataset. The latter is more precised when a sufficient amount of positions is fetched around an airport.

#### How to

Different steps must be followed to obtain the results. 

##### The initial excel file

The operator needs to __create an excel file named "Airport"__ according to this template : 

![Runway_excel_template](https://rosewood.palantircloud.com/blobster/api/salt/ri.blobster.main.image.4a52682e-16ce-4cce-bfd1-8d5819f429c6)

Columns description :

- Airport ID -> ICAO identification of the airport
- Runway QFU -> QFU of the considered runway on that airport
- Runway Magnetic Orientation -> Exact magnetic orientation of the runway as disclosed by the available external sources
- Latitude -> Latitude of the airport
- Longitude -> Longitude of the airport
- Magnetic Variation -> The magnetic variation as disclosed by the available external sources

All this data and especially the data coming from "external sources" must be filled out by the operator with the current knowledge
he has on the runway he wants to study. Some websites like [SkyVectors](https://skyvector.com/airports), [Great Circle Mapper](http://www.gcmap.com/) or [World Aero Data](http://worldaerodata.com/) can be useful to find this data.

When the excel file is created following the above template, it needs to be __uploaded__ in Foundry at this [address](https://rosewood.palantircloud.com/workspace/compass/view/ri.compass.main.folder.1018abe5-4bad-4fed-af49-e08b3541d207).
A simple drag and drop in the opened webpage will upload it.

##### The R script

The remaining step is to run one of the two R scripts in RStudio :

![RStudio button location](https://rosewood.palantircloud.com/blobster/api/salt/ri.blobster.main.image.98a6f99c-2f68-41e8-a539-b99bebbdce59)

The following instruction will show you how to create a project out of this study.

###### Create an RStudio project

1. Copy this link (don't open it): https://rosewood.palantircloud.com/stemma/git/ri.stemma.main.repository.43d7ba08-a6b6-4c8a-839c-c2eba062ed3d/Repository-2017-07-03-14-39-41.
2. In RStudio, create a new project : 

![Project creation instruction](https://rosewood.palantircloud.com/blobster/api/salt/ri.blobster.main.image.6fb2141b-9788-410f-b329-0bdf1a0e3b44)

Paste the link you copied earlier in the repository url box, name your project and click on "create project".

###### Run the script

![Script opening](https://rosewood.palantircloud.com/blobster/api/salt/ri.blobster.main.image.24416ebe-555c-46b9-87b2-2d8e86650761)

1. Click on one of the R script RW_orientation_check_heading_based or RW_orientation_check_track_based and wait for it to be opened.
2. Press Ctrl+alt+R to run the script.

##### Retrieval of the results

The results will be saved at the end of the script run in this [folder](https://rosewood.palantircloud.com/workspace/compass/view/ri.compass.main.folder.1018abe5-4bad-4fed-af49-e08b3541d207) under the 
name of the type of analysis chosen (Heading based or Track based).