# Business Problem

Your company is expanding in to new industries to diversify its portfolio. Specifically, they are interested in purchasing and operating airplanes for commercial and private enterprises, but do not know anything about the potential risks of aircraft. You are charged with determining which aircraft are the lowest risk for the company to start this new business endeavor. You must then translate your findings into actionable insights that the head of the new aviation division can use to help decide which aircraft to purchase.

## Data Source, Data Analysis, and Recommendations

The data for the solving the business problem comes from the National Transportation Safety Board (NTSB).  It includes aviation data from 1962 to 2023.

I obtained the NTSB data from the following link - https://www.kaggle.com/datasets/khsamaha/aviation-accident-database-synopses

I set out to solve the business problem by providing the following three recommendations:

1. Aircraft Manufacturers that should be considered for purchase based upon Fatalities per Aircraft Manufacturer Accident Record

2. Aircraft Manufacturers that should be considered for purchase based upon Major Injuries per Aircraft Manufacturer Accident Record

3. Aircraft Manufacturers that should be considered for purchase based upon Minor Injuries per Aircraft Manufacturer Accident Record


## Exploratory Data Analysis

When I work in pandas, I like to being running exploratory data analysis to become familiar with the dataframe.  I want to understand some of the following attributes:

1. Number of columns
2. Number of rows
3. Columns Names
4. Type of Data within the Columns

Based on the preliminary analysis, the follwing columns: 1) Latitude, 2) Longitude, 3) Airport Code, 4) Airport Name, 
5) Air Carrier have missing data.  I may want to consider removing the columns.  I am going to see how many rows and columns of
data have missing or undefined data.

Based on the following code - df.isna().sum():
    
1) The "Latitude" column is missing data for 54,507 of its rows
2) The "Longitude" column is missing data for 54,516 of its rows
3) The "Aircraft Category" is missing data for 56,602 of its rows
4) The "FAR.Description" is missing data for 56,866 of its rows
5) The "Schedule" column is missing data for 76,307 of its rows
6) The "Air Carrier" column is missing data for 72,241 of its rows

As another check, I am going to examine whether or not there are any rows of duplicate data within the Aviation Data file.

There are no rows of duplicate data within the Aviation Data file.  However, I will remove the following columns - 1) "Latitude, 2) "Longitude", 3) "Aircraft Category", 4) "FAR.Description", 5) "Schedule", and 6) "Air Carrier" - since their missing rows of data represents a majority of the number of rows present in the Aviation Data file.

## Additional and Initial Analysis

I utilized Tableau to conduct additional and initial analysis of the data.

Analysis can be accessed via the following link: https://public.tableau.com/app/profile/keith.otuomagie/viz/aircraft_analysis_kbo_2024_08_03/SafetyRecordperAircraftManufacturer

I examined the following: 

1. Total Number of Fatalities incurred by each Aircraft Manufacturer
2. Total Number of Serious Injuries incurred by each Aircraft Manufacturer
3. Total Number of Minor Injuries incurred by each Aircraft Manufacturer


The top 5 Aircraft Manufacturers that incurred the most fatalities are the following:

1. Cessna (9,641 total fatalities)
2. Boeing (8,748 total fatalities)
3. Piper (6,689 total fatalities)
4. Beech (3,784 total fatalities)
5. Bell (1,332 total fatalities)


The top 5 Aircraft Manufacturers that incurred the most serious injuries are the following:

1. Cessna (4,894 total serious injuries)
2. Piper (3,059 total serious injuries)
3. Boeing (2,157 total serious injuries)
4. Beech (1,095 total serious injuries)
5. Bell (878 total serious injuries)


The top 5 aircraft manufacturers that incurred the most minor injuries are the following:

1. Cessna (6,876 total minor injuries)
2. Piper (3,757 total minor injuries)
3. Boeing (2,761 total minor injuries)
4. McDonnell Douglas (1,505 total minor injuries)
5. Beech (1,122 total minor injuries)

This is not a complete way to determine which aircraft manufacturers have the best (or worst) safety because each aircraft manufacturer has a different amount of records within the Aviation data file.

## Continuing Exploratory Data Analysis

I am going to continue additional exploratory analysis via pandas.  I want to see how many Aircraft Manufacturers are represented in the Aviation Data file.

## Data Cleaning

Examining the following code - df['Make'].value_counts()[0:50] - I see that there are more records for certain Aircraft Manufacturers than others. In order to eventually provide a series of recommendations, I may need to consider a subset of the Aircraft Manufacturers.

I have also made the following observations, which are the following:
1. Cessna is spelled in both capital letters and lower case letters;
2. Piper is spelled in both capital letters and lower case letters;
3. Boeing is spelled in both capital letters and lower case letters;
4. Airbus is represented with the following two spellings - "AIRBUS" and "Airbus Industrie";
5. Douglas is represented with the following two spellings - "Mcdonnell Douglas" and "Douglas";
6. Beech is spelled in both capital letters and lower case letters;
7. Robinson is spelled in both capital letters and lower case letters;
8. Bell is spelled in both capital letters and lower case letters;
9. Grumman is represented with the following two spellings - "Grumman" and "Grumman American";
10. Mooney is spelled in both capital letters and lower case letters;
11. Hughes is spelled in both capital letters and lower case letters;
12. Schweizer is spelled in both capital letters and lower case letters;
13. Aeronca is spelled in both capital letters and lower case letters;
14. Maule is spelled in both capital letters and lower case letters;
15. Bellanca is spelled in both capital letters and lower case letters;
16. Embraera is spelled in both capital letters and lower case letters;
17. Air Tractor is spelled in both capital letters and lower case letters;
18. Luscombe is spelled in both capital letters and lower case letters;
19. De Havilland is spelled in both capital letters and lower case letters;
20. Stinson is spelled in both capital letters and lower case letters;
21. North American is spelled in both capital letters and lower case letters;
22. Sikorsky is spelled in both capital letters and lower case letters.

I am going to format the spelling for all 22 aforementioned companies.

I want to start adding the number of fatalities for each Aircraft Manufacturer.  As noted in the following code - df['Make'].nunique() - there are 8,211 unique Aircraft Manufacturers in the Aviation Data file.  As a result, I do not think it is worthwhile to calculate the number of fatalities for each Aircraft Manufacturer.  I will consider the Aircraft Manufacturers within the top 20 Value Counts.

## Data Normalization

Each Aircraft Manufacturer has a different number of records in the Aviation Data file.  As a result, the data needs to be normalized.  One approach is to calculate the number of Aircraft Manufacturer fatalities, and then divide by the number of Aircraft Manufacturer Records.

![image.png](attachment:image.png)

## 1) Recommendations for Aircraft Manufacturers based upon fatalities per Aircraft Manufacturer Record

Based on the bar chart - Schweizer (0.12), Stinson (0.16), Luscombe (0.17), Air Tractor (0.18), Aeronca (0.19), and Maule (0.19) - have the lowest number of fatalities per Aircraft Manufacturer record.

However, Schweizer, Stinson, Luscombe, Hughes, and Champion are no longer in existence.


Schweizer (0.12) is no longer in existence - https://en.wikipedia.org/wiki/Schweizer_Aircraft

Stinson (0.16) is no longer in existence - https://en.wikipedia.org/wiki/Stinson_Aircraft_Company

Luscombe (0.17) is no longer in existence - https://en.wikipedia.org/wiki/Luscombe_Aircraft

Hughes (0.22) no longer exists - https://en.wikipedia.org/wiki/Hughes_Aircraft_Company

Champion (0.26) was purchased by Bellanca - https://en.wikipedia.org/wiki/Champion_Aircraft 


My recommendation for Aircraft Manufactures are the following: Air Tractor (0.18), a tie between Aeronca (0.19) and Maule (0.19), Grumman (0.26), Bellanca (0.33), and Cessna (0.36).

![image-2.png](attachment:image-2.png)

## 2) Recommendations for Aircraft Manufacturers based upon Serious Injuries per Aircraft Manufacturer Record

Based on the bar chart - Maule (0.11), Air Tractor (0.12), Grumman (0.14), Champion (0.17), Luscombe (0.17) - have the lowest number of serious injuries per Aircraft Manufacturer Record.

However, Champion and Luscomber are no longer in existence.

Champion (0.17) was purchased by Bellanca - https://en.wikipedia.org/wiki/Champion_Aircraft

Luscombe (0.17) is no longer in existence - https://en.wikipedia.org/wiki/Luscombe_Aircraft

Robinson (0.18) is also a helicopter company, not an airplane enterprise - https://www.robinsonheli.com/ 

My recommendation for Aircraft Manufactures are the following: Maule (0.11), Air Tractor (0.12), Grumman (0.14), Cessna (0.18), and a tie between Mooney (0.19) and Bellanca (0.19).

![image-3.png](attachment:image-3.png)

## 3) Recommendations for Aircraft Manufacturers based upon Minor Injuries per Aircraft Manufacturer Record

Based on the bar chart - Air Tractor (0.14); Maule (0.17); Schweizer (0.19); three-way tie between Bellanca (0.23), Champion (0.23), and Luscombe (0.23), and a three-way tie beween Cessna (0.25), Piper (0.25), and Beech (0.25).

However, Schweizer, Champion, Luscombe are no longer in existence.

Schweizer (0.19) is no longer in existence - https://en.wikipedia.org/wiki/Schweizer_Aircraft

Champion (0.23) was purchased by Bellanca - https://en.wikipedia.org/wiki/Champion_Aircraft 

Luscombe (0.23) is no longer in existence - https://en.wikipedia.org/wiki/Luscombe_Aircraft

Robinson (0.26) is a helicopter company, not an airplane enterprise - https://www.robinsonheli.com/.

My recommendation for Aircraft Manufactures are the following: Air Tractor (0.14); Maule (0.17), Bellanca (0.23); a three-way tie beween Cessna (0.25), Piper (0.25), and Beech (0.25); and a two-way tie between Grumman (0.26) and Aeronca (0.26).

# Conclusion

I idenified the Aircraft Manufacturers with the top 20 most records in the Aviation Data file.  Next, I examined the following - Number of Fatalities per Aircraft Manufacturer Record, Number of Serious Injuries per Aircraft Manufacturer Record, and Number of Minor Injuries per Aircraft Manufacturer Record.

1. Regarding Number of Fatalities per Aircraft Manufacturer Record, I recommend the following Aircraft Manufacturers: Air Tractor (0.18), Aeronca (0.19), Maule (0.19), Grumman (0.26) and Bellanca (0.33).

2. Regarding Number of Serious Injuries per Aircraft Manufacturer Record, I recommend the following Aircraft Manufacturers: Maule (0.11), Air Tractor (0.12), Grumman (0.14), Cessna (0.18), and a tie between Mooney (0.19) and Bellanca (0.19).

3. Regarding Number of Minor Injuries per Aircraft Manufacturer Record, I recommend the following Aircraft Manufacturers: Air Tractor (0.14); Maule (0.17), Bellanca (0.23); a three-way tie beween Cessna (0.25), Piper (0.25), and Beech (0.25); and a two-way tie between Grumman (0.26) and Aeronca (0.26).

# Next Steps

Next Steps will consist of the following three items.

1. Aircraft Models

- Within the recommended Aircraft Manufacturers, identify the aircraft models that produce the following: a) least amount of fatalities per accident record; b) least amount of serious injuries per accident record; and c) least amount of minor injuries per accident record.

2. Airbus

- Identify any Airbus models that have safety records in line with recommended aircraft manufacturers

3. Safety

- Identify factors that negatively impact the safety of a flight