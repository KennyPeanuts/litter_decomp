# Leaf Decomposition Experiment Leaf Dry Mass and AFDM 

## Metadata

* Collected by: KF, LT, AC, KP, AG

* Collected on: Fall, Winter, and Spring 2013/2014

* Affiliation: Longwood University

* Location:

    * Daulton Pond (DP)
    * Lancer Park Pond (LPP)
    * Campus Pond (CP)

* Description:

The data were collected as part of an experiment evaluating the mass loss of leaves incubated in ponds.  Leaf packs made of 5 g (dry mass) of Tulip Poplar leaves collected immediately after senescence were placed into plastic mesh bags.  The bags were placed into the littoral zones of the ponds in approximately 0.5 - 1 m of water.

Five randomly chosen bags were collected on each sampling date.  The bags were collected in a 250 um mesh net to prevent loss of macroinvertebrates during collection.  Immediately upon returning to the lab each bag was cut open and the remaining leaves were gently rinsed in tap water over a 1 mm sieve.  All leaf material retained by the sieve was then dried at 50 dC in a pre-weighed paper bag.  All animals and any sediment that passed through the sieve was preserved in 70% EtOH.

The dried leaves were weighed, homogenized with a mortar and pestle and then ashed at 550 dC for 4 h.

* Created: 19 Feb 2014

* Modified: 19 Feb 2014

### Measured Variables:

* lake = the name of the pond

* sample = the identifying number on the bag

* date_col = the day that the bag was removed from the pond

* julian = the julian day of the collection

* year = the year of the collection

* bag = the mass of the empty paper bag (g)

* bag_leaf = the mass of the bag + leaves after 48+ of drying at 50 dC (g)

* days = the number of days the bag was in the lake

* cruc_num = the number of the crucible used for the ashing

* cruc_empty = the mass of the empty crucible (g)

* cruc_full = the mass of the crucible plus the ground dry leaves (g)

* cruc_ash = the mass of the crucible plus the ash following 4 h at 550 dC (g)

### Calculated Variables

* leaf_mass = the mass of the leaves after drying for 48+ h at 50 dC (g)

* leaf_mass_AFDM = the mass of the homogenized leaves before ashing (g)

* ash_mass_AFDM = the mass of the ash following ashing at 550 dC for 4 h (g)

* propOM = the proportion of organic matter in the sample

* AFDM = the leaf dry mass multiplied buy the proportion of OM in the sample (g)

## R Code

### Import Raw Data

    leaf <- read.delim("./data/leaf_dry_mass_fall2013.txt", header = T, stringsAsFactors = F)

### Variable Calculation

    leaf_mass <- leaf$bag_leaf - leaf$bag
    leaf_mass_AFDM <- leaf$cruc_full - leaf$cruc_empty
    ash_mass_AFDM <- leaf$cruc_ash - leaf$cruc_empty
    propOM <- (leaf_mass_AFDM - ash_mass_AFDM) / leaf_mass_AFDM
    AFDM <- leaf_mass * propOM

**These data still need to be checked for errors**

### Make Data Frame

    leaf_calc <- data.frame(leaf, leaf_mass, leaf_mass_AFDM, ash_mass_AFDM, propOM, AFDM)

## Output

    write.table(leaf_calc, "./data/leaf_decomp_calc_2013-14.txt", row.names = F, quote = F, sep = "\t")
