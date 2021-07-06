# (Investigating Covid 19 data)
## by (Ahmed Abdelrahman)


## Dataset

> 

1- Timeseres data:

Four Datasets contains time series data of global confirmed, recovered, deaths and vaccinations cases for all the countries in the world till 17-6-2021.

**Source:** Johns Hopkins Coronavirus Resource Center 'https://coronavirus.jhu.edu/about/how-to-use-our-data

2-Demographic data: consists of merging two datasets including:

1- Country
2- Population
3- Population density (people/Km2)
4- Total tests coducted by each country till 17-6-2021
5- Continent
6- Income level
7- Median age of each country.

**Note:**
Combination of data needed work with spreadsheet, manual entry and modification of data so it will be provided after pereperation.
 
**Sources:** 

A) The United Nations Statistics Division https://unstats.un.org/unsd/demographic-social/products/dyb/index.cshtml#censusdatasets

B) Worldometers https://www.worldometers.info/coronavirus/


## DATA Wrangling

1- confirmed, recovered and deaths dataframes
* They have the same structure but it is untidy structure. So, first I grouped the data by Country/Region to make all
records are related to countries only not to provinces.Then, I worked on making all dates be in one column and so the countries using
Melt function  then I merged the 3 dataframes on country name.

2- Vaccination dataframe

* Again, sum all provinces to get the whole country records for each day.
* Rename columns to match those in the merged dataframe then merge again on country and date.

3- Demographic dataframe 

* Add total_tests_per_million column to the dataframe then drop total_tests column as Total tests is time independant
It is the cummulative tests conducted till 17-6-2020. It has played its role in calculating tests per million columns.

4- Create a function to have columns for daily cases using cummulative case data.

5- By exploring daily data I found negative values and by investigating I discovred Wrong data in the dataframe itself. So I created a func that tried to solve this by 
replacing wrong cummulative values - when it is smaller than that for the day before - with the last value.

ex day1  5000
   day2  0
   day3 5500

so the function will replace 0 as it is smaller than the value before (5000) by exactly the value before (5000) assuming zero daily cases.

6-Create a copy of the final prepared dataframe and add some columns that would help in the investigation.

7-  Finally, add columns that represent two levels of median_age, test per million and population density based on median split to help the analysis.


## Summary of Findings


1- It is clear that the occurrence time of waves and their strength are greatly different from one country to another. We definitly can't identify a pattern that all countries follow either in wave strength or time of occurrence. we can only find few details that some countries share.


2- Worldwide data may be misleading if it took alone as different countries has very different conditions.So, we can't generalize any insights from it.


3- The strength of waves worldwide is continously incrasing but in Egypt,US and Italy the third wave is lower than the second one. This can explain point 2.


4- Egypt, United Kingdom and US shares a wave in months [Dec,Jan,Feb].


5- Egypt and Italy share a repetitive pattern of covid waves that starts between Feb and March. It happened in 2020 and also in 2021.


6- United Kingdom and India don't have  repeatitive patterns in waves till now.


7- There is a wide gap of test rates between countries.


8- High test rates result in increase in daily cases per million ratio. This High test rates will be the more likeliy to represent the actual case.  

9- For low test rates it seems to have no effect.

10 - For high test rates we can see an increase in average daily cases per million for high population density.


11- For both low test rates and high test rates we can see an increase in average daily cases per million for high  median age counties but it is more clear for high test rates.


12- Countries with high Median age has higher averager deaths under all conditions.

13- Countries with low Median age have about the same deaths per million ratio for both population density level.


14-  For Countries with high Median we can see that deaths per million are inversly proportional to population density for both test rates.


15- Under all conditions, we can see the higher the income the higher the cases per million.


16- we can see that even Africa has lower cases per million and deaths per million but has the second highest deaths to confirmed ratio. This can reflect quality of the heath care system of Africa.

17- South America is the most suffering continent.

18- Europe and North America reflect better heath care systems with their low death to confirmed ratios compared to their very high cases per million.

19 - for US and Uk we can notice a high decrease in daily cases from the start of vaccination.


## Key Insights for Presentation

Answers for the following questions

1- What is the behavior of Covid19?

* Are Covid waves till now repeating with a pattern,ie are they coming in specific months?
* Does the waves' strength change or not?

2- How Can we rely on these data to make comparisons and extract conclusions?

3- What is the effect of Population density on daily cases?

4- What is the effect of median age on daily cases?

5- What is the effect of Income Level on daily cases?

6- What is the effect of Continent on daily cases?

7-  What is the effect of Vaccinations on daily cases?

