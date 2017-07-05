# Surface Area and Lat-Long of the Ponds in the Leaf Decomposition Experiment and Litter Density Experiment

## Metadata

* Collected by: KF

* Affiliation: Longwood University

* Description:

The surface area of the ponds was calculated off of google maps using the free tool at [https://www.daftlogic.com/projects-google-maps-area-calculator-tool.htm](https://www.daftlogic.com/projects-google-maps-area-calculator-tool.htm). Each pond was outlined with an abitrary number of points that best described the outline of the pond at the highest zoom that would allow the entire pond to be seen on the screen.

The lat-long of the pond was determined using the ``What's here?'' function on [https://www.google.com/maps](https://www.google.com/maps).

* Created: 5 July 2017

* Modified: 

### Measured Variables:

* lake = the name of the pond

* SA = the surface area of the pond in m^2

* ha = the surface area of the pond in hectares

* lat = the latitude of the appoximate center of the pond (DD)

* long = the longitude of the approximate center of the pond (DD)

## R Code

### Enter Data

    pond <- c("Campus Pond", "Woodland Court Pond", "Daulton Pond", "Wilck's Lake", "Lancer Park Pond") 

    SA <- c(688.97, 3028.37, 5467.51, 131770.35, 1046.75)
    
    ha <- SA * 0.0001
    
    lat <- c(37.297, 37.284, 37.283, 37.304, 37.306)
    
    long <- c(-78.398, -78.392, -78.388, -78.415, -78.404)

### Make Data Frame

    pond <- data.frame(pond, SA, ha, lat, long)

## Output

    write.table(pond, "./data/Decomp_Pond_Area_Location.csv", row.names = F, quote = F, sep = ",")
