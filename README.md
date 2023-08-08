# J124-Final-Project: Data Analysis of Racial and Demographic Trends of High School Education in California, United States.

<h1>Project Description</h1>
In this project, I will be looking into Trends of Graduation and Dropout Rates across Race and Demography in the education system in Caifornia, United States. In doing so, I would be looking specifically into yearly Adjusted Cohort Graduation Rates(ACGR) of High Schools (Grade 9-12) of the Academic Years 2016-2017 to 2021-2022. Through this data, the Yearly Graduation and Dropout Rates across race and demography of schools across all School Districts and Counties in California are retrieved and compared for analysis.

The data is from the California Department of Education and can be found here: [https://www.cde.ca.gov/ds/ad/filesacgr.asp](https://www.cde.ca.gov/ds/ad/filesacgr.asp). 

<h1>Data Pre-processing</h1>
Due to the large number of School Districts and Schools in Califirnia, I will be looking at the Data of the Adjusted Cohort Graduation Rates aggregated by Counties. As I am measuring the data across all school in California, Schools that are both in and not in the Dashboard Alternative School Status Program (DASS) as well as both Charted and Non-Chartere Schools will be included in the analysis.

As the data files are seperated by each Graduation Year on the website, they are all individually downloaded, filtered and merged on Excel, before importing them into Google Sheets for further Data Analysis.

Based on the above stated conditions, the data is filterd as such using Power Query on Excel:
* "AggregateLevel" Column = "C": To filter rows that are only aggregated by the level of Counties.
* "DASS" = "All": To filter rows that contain schools that are both in and not in DASS.
* "CharterSchool" = "All": To filter rows that contain school that are both Charted and Non-Chartered.

After which, the datasets from Academic Year 2016-2017 to 2021-2022 are combinde together to form a single Dataset, named 2017-2022 (County). 
![Pre-processing of Data on Excel Power Query](/images/Power_Query.png )  

As Google Sheets is not able to handle the size of the data, two Googele Sheet Files are created in my analysis. They are as follows:
* [ACGR](https://docs.google.com/spreadsheets/d/1zc8FEzi5wkwPSBJD1SgmVf1vp_lN6pdns5f7aXnaASc/edit?usp=sharing): Looks at the general broad Overview of the data.
* [ACGR Dropout Rates](https://docs.google.com/spreadsheets/d/1wkpduouZsWpbPY3YoUNc3CZhI6z2E4JB492esOP2N-8/edit?usp=sharing): Focuses on the Dropout Rates.

<h1>Analysis Questions</h1>

**Question 1. What are the Top 5 Counties that had the highest Dropout Rates in 2022?**  
_Methodology_  
1: Create a pivot table is created from the data on a seperate sheet, names as County GDE (stands for Graduation, Dropout and Enrolment). This sheet is created in [ACGR](https://docs.google.com/spreadsheets/d/1zc8FEzi5wkwPSBJD1SgmVf1vp_lN6pdns5f7aXnaASc/edit?usp=sharing).
In addition to looking at the Top 5 Counties by Dropout Rate, the Graduation Rate and Proportion of Students still enrolled are included as well for more comprehensive analysis.  
2: The settings of the Pivot Table are set as such:  
   *  Rows: CountyName, Sort by Dropout Rate in Descending Order
   *  Values as: ( an aggegation function will be used, but because all values are unique, any of the functions (min, max, mean) will work.
      * Regular HS Diploma Graduates (Rate)
      * Dropout (Rate)
      * Sill Enrolled (Rate)
   *  Filters:
      * Academic Year: 2021-2022
      * Reporting Category: TA (meaning total)
![Question 1](/images/Question1.png)  

**Answer:**  
The Top 5 Countries with the highest Dropout Rates in 2022 are as follows (from higest to lowest): San Francisco, Nevada, Inyo, Mono, Plumas.



**Question 2. For the Top 5 Countries with the highest Dropout rates in 2022, how did the dropout rates vary from 2017 to 2022? Which country of the 5 had a significant increase in Dropout Rates after 2019(after Covid 19 Pandemic)?**
_Methodology_  
1. Create a Pivot Table from the data on a seperate sheet, named County Yearly Dropout. This sheet is created in [ACGR Dropout Rates](https://docs.google.com/spreadsheets/d/1wkpduouZsWpbPY3YoUNc3CZhI6z2E4JB492esOP2N-8/edit?usp=sharing).
2. The settings of the Pivot Table are set as such:
   *  Rows: Academic Year
   *  Columns: County Name
   *  Values as: 
      * Dropout (Rate)
   *  Filters:
      * Reporting Category: TA (meaning total)
      * Count Name: Inyo, Mono, Nevada, Plumas, San Francisco
    
![Question 2 Pivot Table](/images/Question2.png)

4. Create a Chart from the Pivot Table. 
![Dropout Rates of Top 5 Countries from 2018-2022](/images/Dropout Rates of Top 5 Countries from 2018-2022.png )

**Answer:**  
Interestingly, most of the 5 countries had a decrease in Dropout Rates between 2018-2019 to 2019-2020, except Mono which had a significant increase in Dropout Rate in that period. Following up from 2019-2020, it is worth noting that the Dropout rates of San Francisco County gradually increased from 2019-2020 to 2021-2022.  



**Question 3. For the Top 5 Countries with the highest Dropout rates in 2022, how did the Dropout Rates vary across Race from 2017 to 2022?**  
_Methodology_  
1. Create a Pivot Table from the data on a seperate sheet, named Race Yearly Dropout. This sheet is created in [ACGR Dropout Rates](https://docs.google.com/spreadsheets/d/1wkpduouZsWpbPY3YoUNc3CZhI6z2E4JB492esOP2N-8/edit?usp=sharing).
2. To answer this question, I created a Pivot Table and Chart for each of the Top 5 Coutnies from Question 1. The settings of the Pivot Table for San Francisco, for example, are set as such:
   *  Rows: Academic Year
   *  Columns: Reporting Category
   *  Values as: 
      * Dropout (Rate)
   *  Filters:
      * Reporting Category: RB, RI, RA, RF, RH, RD, RP, RT, RW
      * County Name: San Francisco


The abbreviations of the Reporting Catergories represents Race and are as such:  
* RB = African American
* RI = American Indian or Alaska Native
* RA = Asian
* RF = Filipino
* RH = Hispanic or Latino
* RD = Not Reported
* RP = Pacific Islander
* RT = Two or More Races
* RW = White
Details of the Reporting Catgories can be found [here](https://www.cde.ca.gov/ds/ad/fsacgr.asp).  

![Race Yearly Dropout](/images/Race_Yearly_Dropout.png "Race Yearly Dropout")  

3. Create a line chart with the table, with the Academic Year as the X-axis, and a series fro each individual reporting category (RB, RI, RA, RF, RH, RD, RP, RT, RW).
4. Repeat steps 2 and 3 for the other 4 counties.

**Answer:**\
The charts of Dropout Rates by Race for each of the Top 5 Counties from 2017-2022 are as follows:  
![Dropout Rates across different Races in San Francisco County from 2017-2022](/images/Dropout_Rates_across_different_Races_in_San_Francisco_County_from_2017-2022.png)
![Dropout Rates across different Races in Nevada County from 2017-2022](/images/Dropout_Rates_across_different_Races_in_Nevada_County_from_2017-2022.png)
![Dropout Rates across different Races in Inyo County from 2017-2022](/images/Dropout_Rates_across_different_Races_in_Inyo_County_from_2017-2022.png)
![Dropout Rates across different Races in Mono County from 2017-2022](/images/Dropout_Rates_across_different_Races_in_Mono_County_from_2017-2022.png)
![Dropout Rates across different Races in Plumas County from 2017-2022](/images/Dropout_Rates_across_different_Races_in_Plumas_County_from_2017-2022.png)

From the charts, it can be observed that African Americans(RB) and Hispanics/Latino (RH) are the races that often have the highest dropout rates. It is worth noting that San Francisco and Nevada Counties have both a more balanced mixture of Races in their Dropout Rates, while for Inyon, Mono and Plumas Counties, there is only African American (RB), Hispanic/Latino (RH), and White Americans (RW) in their Dropout Rates.  




**Question 4. For the Top 5 Countries with the highest Dropout rates in 2022, how did the Dropout Rates vary across Demographic Background (Homeless, Disabilities, English Learners, etc) from 2017 to 2022?**  

_Methodology_  
The Methodology for this question is similar to Question 3, just that the Filtes fro Reporting Categories are the Demographic Categories instead.
1. Create a Pivot Table from the data on a seperate sheet, named Demographic Yearly Dropout. This sheet is created in [ACGR Dropout Rates](https://docs.google.com/spreadsheets/d/1wkpduouZsWpbPY3YoUNc3CZhI6z2E4JB492esOP2N-8/edit?usp=sharing).
2. To answer this question, I created a Pivot Table and Chart for each of the Top 5 Coutnies from Question 1. The settings of the Pivot Table for San Francisco, for example, are set as such:
   *  Rows: Academic Year
   *  Columns: Reporting Category
   *  Values as: 
      * Dropout (Rate)
   *  Filters:
      * Reporting Category: SE, SD, SS, SM, SF, SH
      * County Name: San Francisco


The abbreviations of the Reporting Catergories represents Demographic and are as such:  
* SE = English Learners
* SD = Students with Disabilities
* SS = Socioeconomically Disadvantaged
* SM = Migrant
* SF = Foster
* SH = Homeless
Details of the Reporting Catgories can be found [here](https://www.cde.ca.gov/ds/ad/fsacgr.asp).  

![Alt text](/Demographic Yearly Dropout.png "Demographic Yearly Dropout")  

3. Create a line chart with the table, with the Academic Year as the X-axis, and a series for each individual reporting category (RB, RI, RA, RF, RH, RD, RP, RT, RW).
4. Repeat steps 2 and 3 for the other 4 counties.

**Answer:**  
The charts of Dropout Rates by Demographic for each of the Top 5 Counties from 2017-2022 are as follows:
![Dropout Rates across different Demographics in San Francisco County from 2017-2022](/images/Dropout_Rates_across_different_Demographic_in_San_Francisco_County_from_2017-2022.png)
![Dropout Rates across different Demographics in Nevada County from 2017-2022](/images/Dropout_Rates_across_different_Demographics_in_Nevada_County_from_2017-2022.png)
![Dropout Rates across different Demographics in Inyo County from 2017-2022](/images/Dropout_Rates_across_different_Demographic_in_Inyo_County_from_2017-2022.png)
![Dropout Rates across different Demographics in Mono County from 2017-2022](/images/Dropout_Rates_across_different_Demographics_in_Mono_County_from_2017-2022.png)
![Dropout Rates across different Demographics in Plumas County from 2017-2022](/images/Dropout_Rates_across_different_Demographics_in_Plumas_County_from_2017-2022.png)

From the charts, it can be observed that Homeless(SH) students had the highest dropout rates for all 5 counties except for Nevada in 2022. It was interesting to see that for Nevada County, the top 3 Demogrphic Groups in Dropout Rates are Enligsh Learners(SE), Socioeconimically Disadvanteged (SS) and Foster (SF). It also important and worrying to note that the Dropout Rates for English Learners in Nevada County were the highest among all other Demographics and Counties in the 5 Counties.  

Another interesting observation was that unlike the other Counties, the Droprates of Inyo County varied consistently among the various Demographic Subgroups through the whole period from 2016-2017 to 2021-2022.  



**Question 5: For the Top 5 Countries with the highest Dropout rates in 2022, which County had the highest Proportion of Senior Year Students who are still enrolled and which County had the lowest graduation rate?**  
_Methodology_  
1: Create a pivot table from the data on a seperate sheet, named as 2022 GDE (stands for Graduation, Dropout and Enrolment). This sheet is created in [ACGR](https://docs.google.com/spreadsheets/d/1zc8FEzi5wkwPSBJD1SgmVf1vp_lN6pdns5f7aXnaASc/edit?usp=sharing).
2: The settings of the Pivot Table are set as such:
   *  Rows: CountyName
   *  Values as: ( an aggegation function will be used, but because all values are unique, any of the functions (min, max, mean) will work.
      * Regular HS Diploma Graduates (Rate)
      * Dropout (Rate)
      * Sill Enrolled (Rate)
   *  Filters:
      * Academic Year: 2021-2022
      * Reporting Category: TA (meaning total)
      * Count Name: Inyo, Mono, Nevada, Plumas, San Francisco

![Question 5](/images/Question5.png)  

**Answer:**  
![Graduation, Still Enrolled and Dropout Rates of Counties in 2022](/images/Graduation,_Still_Enrolled_and_Dropout_Rates_of_Counties_in_2022.png)  
From the chart, it can be seen that Mono has the Highest Proportion of Students were still enrolled after their Senior Year, and also the lowest Gradaution Rate in 2022.


<h1>Data Visualization</h1>  

![Chloropeth Map of High School Dropout Rates of Counties in California in 2022](/images/Chloropeth-dropout-rates-of-high-schools-in-counties-of-california-in-2022.png)

[Chloropeth Map of High School Dropout Rates of Counties in California in 2022](https://datawrapper.dwcdn.net/ROyZZ/3/)

<h1>Interviewees</h1>  
At the end of the project, I hope to interview the following people whom I would believe would find this project useful in allocating resources and implementing policies to help support social subggroups that may be racially or financially disadvangted in their high school education.  

1. Dr. Matt Wayne, Superintendent of San Francisco Unified School District
    *  Phone: (415) 241-6121
    *  Email: waynem@sfusd.edu
2. Scott W. Lay, Nevada County Superintendent of Schools
    *  Phone: (530) 478-6400
    *  Email: lscott@nevco.org
