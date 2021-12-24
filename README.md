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

## CASE STUDY: Calgary Community Crime Statistics (updated Nov 2021)
LINK TO DATASET: https://data.calgary.ca/Health-and-Safety/Community-Crime-Statistics/78gh-n26t/data

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

## CASE STUDY: Swedish airpots passenger traffic from 2019 to Nov 2021
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

## PROJECT: May the force be with you
### Overview
Power Bi really got the force of data cleaning and automation.
The report uses a web service, [SWAPI](https://swapi.dev/) – The Star Wars API to import all the characters from Star Wars, it then appends multiple JSON pages (thru query functions), calculates their BMI, and builds relationship between characters and species to get further insights by species.
### Goal and Objectives
Import the tables from the API, cleaning the first one and then using M code to create parameters and functions to automate the process for all the other tables to import.
Create a “what if” parameter on the main visual to allow the user to get a custom result on calculations.
### Method
-Getting the “people” into Power BI importing data from web starting from page 1: https://swapi.dev/api/people/?page=1 
-renaming the query “SW_People_page1”, transforming the list into a table and expanding
-selecting only the columns to keep and replacing null / n/a values
From “source” rc on the count of people to get a “new query” renamed “PeopleCount”
-to import a total of 9 pages, we created a blank query renamed “people” and generated a dynamic list = List.Numbers(1, PeopleCount/10) that we then transformed into a table; change the values type to “text”
-we created a New Parameter “PageNmb”, type text, value 1
-back to the first query “SW_People_page1”, source, we cancelled the value “1” and concatenated (&) the “PageNmb” parameter
-transformed the query “SW_People_page1” into a function named “GetPeople” to get the other 9 pages
-in the “people” query we invoked our custom function “GetPeople” and expanded the new column
-removed characters from the column “species’
-replaced “unknown” with 0 in “height” and “mass” columns; changed column types
-transformed the height values in meter by dividing them by 100
-we create a custom column for BMI: =[mass in Kg]/Number.Power([height in meters],2), changed the column type to decimal
-used the same method to get “Species” (webContent https://swapi.dev/api/species?page=" & PageNumber))
-imported the table BMI from Wikipedia: https://en.wikipedia.org/wiki/Body_mass_index , kept only necessary columns with reference to ranges of different categories of BM
-loaded data for the query “people” into the report
-added DAX column “Category” to people based on BMI classification:  Category = SWITCH(TRUE(), people[BMI]<=15, "Very severely underweight", people[BMI]<16,  "Severely underweight", people[BMI]<18.5, "Underweight", people[BMI]<25, "Normal (healthy weight)", people[BMI]<30, "Overweight", people[BMI]<35, "Obese Class I (Moderately Obese)", people[BMI]<40, "Obese Class II (Severely Obese)", "Obese Class III (Very Severely Obese)")
-using the treemap, we have “name” on “group”, “BMI” on “values”
-we created a measure Count of People = COUNTROWS(People) to use in a visual with “species” and in another with “category”
-using the “what if factor” we got a “Droid Factor” parameter, starting at 0.1, ending at 1 with increment of 0.1 (this will allow the user flexibility to increment the BMI for the droids on a slider, since droids are made of metal, therefore heavier than other species with regular BMI)
-we wrapped the Droid factor parameter into a measure “Droid BMI” = [BMI2] * 'Droid Factor'[Droid Factor Value]
- then we created a measure “Galactic BMI” to assess the BMI of droids based on their custom “Droid BMI” and the BMI of Hutts (10% of average BMI) creating the measure: Galactic BMI = AVERAGEX (VALUES(Get_Species), SWITCH (Get_Species[name], "Droid", [Droid BMI], "Hutt", [BMI2]/10, [BMI2]))

