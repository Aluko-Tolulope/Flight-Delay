# Flight-Delay
### Project Overview
This repository presents a comprehensive analysis of flight delay patterns within the United States during 2015. The project was undertaken as part of the Data Analyst Track at Quantum Analytics, aiming to apply data-driven methodologies to uncover actionable insights from a complex dataset.

By leveraging statistical analysis and data visualization techniques, this study seeks to identify key factors contributing to flight delays, assess their impact on airlines and airports, and develop potential strategies for delay mitigation. The findings of this project contribute to a deeper understanding of the aviation industry's challenges and opportunities for improvement.

### Expected Outcome
Some of the outcome include
- Pinpointing the most frequent reasons for flight disruptions.
- Identifying patterns in delay occurrences over time, such as seasonal variations or specific days of the week.
- Comparing delay rates across different airlines to identify best practices.
= Assessing the impact of airport operations on flight delays.
- Potentially creating models to forecast flight delays based on identified patterns.
- Providing actionable insights to airlines, airports, and air traffic control for delay reduction.
Ultimately, the goal is to deliver a comprehensive understanding of flight delays, enabling data-driven decision-making to enhance the passenger experience and optimize airline operations.

### Tools
Microsoft Power BI


### Data Preparation
To establish a comprehensive dataset for analysis, the airline, airport, flight, and cancellation code tables were merged. Rigorous data cleaning processes were implemented to ensure data accuracy and consistency. This involved handling missing values, standardizing data formats, and resolving inconsistencies across datasets. The resulting integrated dataset served as the foundation for subsequent exploratory data analysis.

### Data Cleaning and Visualization
in this stage,
- Checked the values and data quality to identify missing data, inconsistencies and Outliers.
- Carried out cross verification checks and logical checks
- The tables were merged with the use of primary and foreign keys and the new base table is labelled as Consolidated
- Added conditional columns to call out months and days of the weeks
### Data Visualization
This was done using DAX concepts(Calculated measures, Calculated column,etc), Visuals/Charts,Filters and slicers etc in Power BI

### 1: What is the total number of flights recorded in the year 2015?
The dataset encompasses an impressive 6 million flight records spanning the entirety of 2015. This substantial volume of data provides a rich foundation for in-depth analysis of flight operations, delays, and performance metrics throughout the United States. By examining such a large dataset, we can uncover meaningful trends, patterns, and anomalies that would otherwise be obscured by smaller sample sizes. we are able to determine this using this code
```  Total Flights =
               COUNT
                  ('Consolidated table'[FLIGHT_NUMBER])
```

### 2: What is the total number of cities covered in the year 2015?
The flight delay dataset spans across a network of 309 US cities, providing a comprehensive overview of domestic flight operations within the country during 2015. This was gotten by calculating the distinct count of city as shown in the code snippet
``` Total cities =
                DISTINCTCOUNT
                        ('Consolidated table'[airports.CITY])
```
### 3: What are the total airports covered?
The dataset encompasses a total of 323 airports across the United States, we were able to determine this using the DAX formula below
```Total Airports =
                DISTINCTCOUNT
                            ('Consolidated table'[airports.AIRPORT])
```
### 4: What are the airline covered in the report?
The dataset encompasses a total of 4898 airline across the United States, we were able to determine this by doing a distinct count of the flight's tail number using the DAX formula below
```   Total Airline =
                   DISTINCTCOUNT('Consolidated table'[TAIL_NUMBER])
```
### 5: What is the number of cancelled flights?
Our analysis revealed a total of 89884 cancelled flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific cancellation code
```Cancelled Flights = CALCULATE
                          ([Total Flights],'Consolidated table'[CANCELLED])
```
### 6: What is the percentage of cancelled flights?
Our analysis revealed a total of 1.54% cancelled flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific cancellation code
```Percentage Cancelled =
         CALCULATE([Cancelled Flights]/[Total Flights])
```
### 7: What is the number of delayed flights?
Our analysis revealed a total of 2213109 delayed flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific delayed code
```Delayed Flight =
              CALCULATE([Total Flights],'Consolidated table'[delay status] ="Late")
```
### 8: What is the percentage of delayed flights?
Our analysis revealed a total of 38.03% delayed flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific delayed code
```Percentage Delayed =
                  CALCULATE([Delayed Flight]/[Total Flights])
```
### 9: What is the number of diverted flights?
Our analysis revealed a total of about 151817  diverted flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific diverted code
``` Diverted =
            CALCULATE([Total Flights],'Consolidated table'[DIVERTED])
```
### 10: What is the percentage of diverted flight?
Our analysis revealed a total of about 0.26%  of the total flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a specific diverted code
```percentage Diverted =
                CALCULATE([Diverted]/[Total Flights])
```
### 11: What is the total number flight that are on-time?
Our analysis revealed a total of about 3500899  flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a on-time code
```Total Flights Ontime =
                  CALCULATE([Total Flights],'Consolidated table'[delay status] ="On Time")
```
### 12: What is the percentage of On-time flights?
Our analysis revealed a total of about 60.16%  flights within the 2015 dataset.To calculate this figure, a DAX formula was employed to filter the dataset for records with a on-time code
``` Percentage On time =
              CALCULATE([Total Flights Ontime]/[Total Flights])
```

### Key Insights
 By examining delay patterns, causal factors, and their impact on airlines and airports, valuable insights can be extracted to inform operational improvements.

Key areas of focus include:
-High on-time performance: Approximately 60% of flights arrived on time.
- Extensive data coverage: About 6 million flights across 309 cities and 323 airports.
- Delay Hotspots: The map identifies regions with frequent flight disruptions. Texas and California experience the highest rates of delays, followed by Illinois, Georgia, Florida, and New York. 
- Airline performance comparison: Enables evaluation of airline operational efficiency.
- Weekday Consistency: There seems to be a relatively consistent number of flights across weekdays, with slight variations.
  





