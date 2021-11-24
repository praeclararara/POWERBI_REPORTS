# POWERBI_REPORTS
## CASE STUDY: Canadian Disaster database: https://www.publicsafety.gc.ca/cnt/rsrcs/cndn-dsstr-dtbs/index-en.aspx 
Digital transformation, automation and AI are all data-driven. Open data is a trendy concept in data economy.
It presents businesses with a huge opportunity to use half of the world's data to make better decisions.
Open data also poses a huge challenge as it is often raw, messy, complex, not analyzable, not consumable...
The world needs capable data analysts who can go out there hunting for data, make data available and easy to consume.
From the data vendor's perspective, making data publicly accessible helps generate inbound traffic and improve user loyalty.
The value proposition is not about data itself. It's about curation, availability and usability of data.
It goes from needing data to having data in seconds. On the other hand, data consumers can leverage open data and combine it with internal data to generate insights and create values for the economy. In this course, you will use data found on Government of Canada Open Data Portal and apply most practical tools and techniques to make open data consumable, visualize trends and patterns,
and present conclusions and recommendations to general public.

## CASE STUDY: Titanic dataset analysis
### Background
On April 10, 1912 the RMS Titanic left Southhampton, England headed for New York. Aboard were 2,435 passengers and 892 crew members. Five days later, about 20 minutes before midnight, the Titanic hit an iceberg in the frigid waters about 375 miles south of New Foundland. Within approximately two and a half hours the ship had split apart and sunk, leaving just over 700 survivors.
### Dataset used
LINKS: https://hatfullofdata.blog/wp-content/uploads/2020/10/TitanicLocations.xlsx
       https://hatfullofdata.blog/wp-content/uploads/2020/10/titanicdata.csv
### Notes about the Dataset     
Pclass: A proxy for socio-economic status (SES)
1st = Upper
2nd = Middle
3rd = Lower

Age: Age is fractional if less than 1. If the age is estimated, is it in the form of xx.5

SibSp: The dataset defines family relations in this way...
Sibling = brother, sister, stepbrother, stepsister
Spouse = husband, wife (mistresses and fiancés were ignored)

Parch: The dataset defines family relations in this way...
Parent = mother, father
Child = daughter, son, stepdaughter, stepson
Some children travelled only with a nanny, therefore parch=0 for them.

### QUESTIONS the analysis wants to answer
- Did passenger class made any difference to his survival?
- Which gender had more survival?
- Person travelling with others had more survival possibility?
- Which age group had better chance of survival?
- What was male and female survival per class and by age?

## CASE STUDY: Swedish airpots passenger trafic from 2019 to Nov 2021
### Datasets used
LINKS: https://www.transportstyrelsen.se/sv/luftfart/Statistik/Flygplatsstatistik-/ 
2021
https://www.transportstyrelsen.se/globalassets/global/luftfart/statistik_och_analys/flygplatsstatistik-excelfiler/211112-passagerarfrekvens-per-flygplats.xlsx 
2020
https://www.transportstyrelsen.se/globalassets/global/luftfart/statistik_och_analys/flygplatsstatistik-excelfiler/210114-passagerarfrekvens-per-flygplats.xlsx 

2019
https://www.transportstyrelsen.se/globalassets/global/luftfart/statistik_och_analys/flygplatsstatistik-excelfiler/210115-passagerarfrekvens-per-flygplats.xlsx

COVID CASES: https://datahub.io/core/covid-19 from 2020 to 2021

### Notes about the Dataset
The datasets are storing yearly passenger traffic thru each of the Swedish airports. Each year is a table, each airport is a sheet of the woorkbook.
The workbooks are not structured tables that can be easly read by Power BI, so they require a COMPLEX CLEANING PROCESS.
A FUNCTION wascreated in order to speed up the work and clean data on multiple excel sheets. 
A FUNCTION was created to import multiple workbooks in Power BI and clean all the sheets using the same Power Query function.
The columns were renamed with English translation to make the info available to a larger public.

The Covid cases dataset was cleaned, filtered and imported in Power BI and linked to the other tables thru a new calendar table that was created in Power BI.

### Analysis
As expected, there has been a deep dive on passenger traffic from 2019 due to Covid-19 with international traffic paying an higher price than domestic traffic.

However the report shows an increase of the number of travelers starting from May 2021 despite the numbers of confirmed cases of Covid-19 where close to the ones for the months of 2020 Summer.
Probably these factors influenced the higher mobility:
-Sweden removed travel restrictions against their Nordic neighbors from May 2021;
-travelers from other EU/EEA countries had permission to enter Sweden upon presenting a negative Covid-19 test thru June but the recommendation to get tested again upon arrival and self-isolate from seven days was relaxed from June 1.
-On 5 May 2021, the Stockholm region began its phase 4, opening up vaccination slots to people aged 55 to 59. On 14 June 2021, over half of Swedish adults had received at least one vaccine dose, with 27% fully vaccinated (source Wikipedia: https://en.wikipedia.org/wiki/COVID-19_vaccination_in_Sweden )
