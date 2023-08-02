# J124-Final-Project: Data Analysis of Racial and Demographic Trends of High School Education in California, United States.

<h1>Project Description</h1>
In this project, I will be looking into Trends of Graduation and Dropout Rates across Race and Demography in the education system in Caifornia, United States. In doing so, I would be looking specifically into yearly Adjusted Cohort Graduation Rates(ACGR) of High Schools (Grade 9-12) of the Academic Years 2016-2017 to 2021-2022. Through this data, the Yearly Graduation and Dropout Rates across race and demography of schools across all School Districts and Counties in California are retrieved and compared for analysis.

The data is from the California Department of Education and can be found here: [https://www.cde.ca.gov/ds/ad/filesacgr.asp](https://www.cde.ca.gov/ds/ad/filesacgr.asp). 

<h1>Data Pre-processing</h1>
Due to the large number of School Districts and Schools in Califirnia, I will be looking at the Data of the Adjusted Cohort Graduation Rates aggregated by Counties. As I am measuring the data across all school in California, Schools that are both in and not in the Dashboard Alternative School Status Program (DASS) as well as both Charted and Non-Chartere Schools will be included in the analysis.

As the data files are seperated by each Graduation Year on the website, they are all individually downloaded and put together on Excel, before importing them into Google Sheets for further Data Analysis.

Based on the above stated conditions, the data is filterd as such using Power Query on Excel:
* "AggregateLevel" Column = "C": To filter rows that are only aggregated by the level of Counties.
* "DASS" = "All": To filter rows that contain schools that are both in and not in DASS.
* "CharterSchool" = "All": To filter rows that contain school that are both Charted and Non-Chartered.

After which, the datasets from Academic Year 2016-2017 to 2021-2022 are combinde together to form a single Dataset, named 2017-2022 (County). 
![Alt text](/Power_Query.png "Pre-processing of Data on Excel Power Query")  

As Google Sheets is not able to handle the size of the data, two Googele Sheet Files are created in my analysis. They are as follows:
* [ACGR](https://docs.google.com/spreadsheets/d/1zc8FEzi5wkwPSBJD1SgmVf1vp_lN6pdns5f7aXnaASc/edit?usp=sharing)
* [ACGR Dropout Rates](https://docs.google.com/spreadsheets/d/1wkpduouZsWpbPY3YoUNc3CZhI6z2E4JB492esOP2N-8/edit?usp=sharing)

<h1>Analysis Questions</h1>

*Question 1. What are the Top 5 Counties that had the highest Dropout Rates in 2022?*

_Step by step methodology_
1. Upload the file onto Google Sheets. The sheet with the data is named as 2017-2022(County)
In addition to looking at the Top 5 Counties by Dropout Rate, the Graduation Rate and Proportion of Students still enrolled are included as well for more comprehensive analysis.
2. Create a pivot table is created from the data on a seperate sheet, names as County GDE (stands for Graduation, Dropout and Enrolment)
3. The settings of the Pivot Table are set as such:
   *  Rows: CountyName
   *  Values as: 
      * Regular HS Diploma Graduates (Rate)
      * Dropout (Rate)
      * Sill Enrolled (Rate)
   *  Filters:
      * Academic Year: 2021-2022
      * Reporting Category: TA (meaning total)
![Alt text](/Question1.png "Question 1")  

Question 2. For the Top 5 Countries with the highest Dropout rates in 2022, how did the dropout rates vary from 2017 to 2022? Which country of the 5 had a significant increase in Dropout Rates after 2019?


Question 3. For the Top 5 Countries with the highest Dropout rates in 2022, how did the Dropout Rates vary across Race from 2017 to 2022?


Question 4. For the Top 5 Countries with the highest Dropout rates in 2022, how did the Dropout Rates vary across Demographic Background from 2017 to 2022?


Question 5. For the Top 5 Countries with the highest Dropout rates in 2022, which County had the highest Proportion of Senior Year Students who are still enrolled and which County had the lowest graduation rate?

<h1>Interviewees</h1>
At the end of the project, I hope to interview the following people whom I would believe would find this project useful in allocating resources and implementing policies to help support social subggroups that may be racially or financially disadvangted in their high school education.

1. Scott Francis, Superintendent of Berkeley School District
    *  Phone: (248) 837-8004
2. Dr. Kyla Johnson-Trammell, Superintendent of Oakland Unified School District
    *  Phone: (510) 879-8000
    *  Email: superintendent@ousd.org
3. Alberto M. Carvalho, Superintendent of Los Angeles Unified School 
District
    *  LinkedIn: https://www.linkedin.com/in/alberto-carvalho-33aa66193/
