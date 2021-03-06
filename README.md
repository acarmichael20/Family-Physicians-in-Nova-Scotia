## Introduction
Health care is an important part of achieving quality of life and optimal health outcomes in Nova Scotia. Traditionally, people access the healthcare system through their Family Physician.  As of April 1, 2020, [46,051](http://www.nshealth.ca/sites/nshealth.ca/files/finding_a_primary_care_provider_in_nova_scotia_report_april_2020.pdf) Nova Scotians have indicated that they are unable to find a Family Physician.
This report will look at:

-The distribution of Family Physicians in Nova Scotia. <br>
-The possibility of a Family Physician shortage due to retirements.

## Data

### The Forward Sortation Area
This report relies heavily on data that has been segmented by geographic region.  The fundamental unit is the Forward Sortation Area (FSA).  The FSA is the first half of a Canadian Postal code. *ie. **B3K** 2T3*. Statistics Canada publishes some data by linking it with an FSA.  Statistics Canada also publishes a GIS file containing the [FSA boundaries](https://www150.statcan.gc.ca/n1/en/catalogue/92-179-X) of Canada.

![Nova Scotia Forward Sortation Areas](NovaScotiaFSA.jpeg)

### Population
The distribution of Nova Scotia’s population was obtained from Statistics Canada’s [Population and Dwelling Count Highlight Tables, 2016 Census]( https://www12.statcan.gc.ca/census-recensement/2016/dp-pd/hlt-fst/pd-pl/Table.cfm?Lang=Eng&T=1201&S=22&O=A)

### Family Physician Data
The data pertaining to Physicians was obtained through the [College Of Physicians & Surgeons Of Nova Scotia](https://cpsns.ns.ca/) (CPSNS).  Using the Physician search page, users can download a .CSV file of summary information on every Physician practicing in Nova Scotia.  While the file contains useful information, it does not contain all the information available on the site. A simple web scraper was scripted using RStudio and the package rvest to obtain the following from CPSNS:

-Each Physician's graduation year. <br>
-Each Physician's business address.  

## ETL, Calculation and Graphics
All ETL, calculations and graphics were performed using a script written in RStudio.

## Distribution of Family Physicians in Nova Scotia
Analyzing the number of Family Physicians with the population in each FSA enables the calculation of Family Physicians per 100,000 people in each area.  This metric is used to colour code each FSA according to the Family Physicians per 100k.  The map is shown below.

![Doctors Per 100K](DocsPer100K.jpeg)

In the above map, there are are grey coloured areas.  These are areas where a Family Physician is not practicing.  These areas are in Eastern Cape Breton and close to the HRM and Truro.  The areas around the HRM and Truro could be explained due to their proximity to a large population center with greater Family Physician coverage.  The lack of a Family Physician in Eastern Cape Breton is less likely due to its proximity to Sydney given its large geographic area.  It may be an area that is genuinely in need of Family Physicians.<br><br>

The geographic area covered by each FSA can vary significantly.  The difference in FSAs can lead to some areas being obscured.  By associating each FSA with a community, it is possible to group the FSAs and make comparisons.

![FamDocPer100KGrouped](FP100K_Com.jpeg)

Surprisingly, the communities making up the HRM, are not the majority of communities with the highest number of Family Physicians per 100,000 people. The top four communities do have a common factor; they are all communities that contain at least one University.

## Estimating Family Physician Retirements
By using the year a Physician graduated from Medical School, it is possible to estimate their age.  Though we should appreciate that there is a spectrum of age at entry to Medical School.  <br><br>The data retrieved from the College Of Physicians & Surgeons Of Nova Scotia contains the date and reason a Physician has inactivated their license.  Using this information, the average retirement age for a Family Physician was calculated to be 64.3 years.<br><br>
Applying the calculated retirement age to the active Family Physicians in Nova Scotia, it is possible to estimate how many of these Physicians are within five years of retirement.  Assuming that retiring Family Physicians will not be replaced, it is possible to predict which communities may face a Family Physician shortage due to retirements, in the next five years.

![RetiringWithin5Years](Retirements.jpeg)

From the above chart, the top three communities that could be impacted by Family Physician retirements are Enfield, Liverpool and New Glasgow.

## Conclusion
This report could be used by the Province of Nova Scotia to help predict Physician manpower requirements and to aid in the recruitment of Family Physicians.
