# Pandas-School-Data

### Summary | GRADE: A
For this project I was given starter csv's containing data from a fictional school district, which included data about each school and each student. I used the Python module Pandas to aggregate the data in a variety of dataframes to provide more insight, See below on the exact dataframes I created and an analysis of the final product.

### Project Writeup

The first step was importing dependencies and loading in the csvs to a pandas dataframe. I also created new boolean columns that indicated whether a student passed reading and math exams. This made it easier to filter later on.

#### District Summary
For the district summary dataframe, I calculated each element in its own line including a count() for schools, a sum() for students and total budget, a mean() for average scores, and a sum with a percent calculation for the percent passing math and reading. I took each element and put it into a new dataframe with the proper formatting.

![District Summary](images/District_Summary.png)

#### Schools Summary
For the school dataframe, the data requirements were the same as the above secion, but grouped by school. First I created a new column which calculated the budget per student by diving the school budget by student count. Then I grouped the student scores by school with a mean() aggregate function, putting that into a new dataframe. These two dataframes were merged to get one full dataframe with all the data. Next, I filtered to the students passing each type of test and translated that into a percent. Once all this information was in the dataframe, I used formatting on the table.

![School Summary](images/School_Summary.png)

#### School Performance
The top and bottom five schools by scores was created by sorting the above dataframe, one by ascending score and one by descending score, then cutting each off with the top five rows.

##### Top Schools
![Top Schools](images/Top_Schools.png)

##### Bottom Schools
![Bottom Schools](images/Bottom_Schools.png)

#### Test Scores by Grade
To get each score by grade level, I first filtered each grade into its own table. Then I grouped by school name with a mean() aggregation. Once that table was create, I extracted the math scores for one table and the reading scores for the other. 

##### Math Scores
![Math](images/Math_Scores.png)

##### Reading Scores
![Reading](images/Reading_Scores.png)

#### School Spending
Grouping schools by spending required setting up bins for each budget range, which were < 600, 600-625, 625-650, and >650. Once those bins were created, I used pd.cut() to cut along the bin lines. 

![School Spending](images/School_spending.png)

#### School Size
A similar process as school spending was used for the grouping by school size. These bins were defined as <2000, 2000-3000, 3000-4000, and >4000 students.

![School Size](images/School_size.png)

The final analysis of observable trends are shown below and also in markdown cells in the code file.


### Analysis

#### Observable Trend 1:

Schools that spend less money (625 or less) per student show a clear increase in test performance relative to those school that spend more (625 or more) per student. The difference is most pronounced in math scores. 

This is a counterintuitive finding, but it may be correlated to school size. In general, schools that have less spending per student also have a smaller student population (see "School Summary"). Schools that are smaller tend to have better test outcomes (see "Scores by School Size"). Given this correlation, it woud be a mistake to conclude that less spending yields increased performance; rather small school sizes (and likely smaller classroom sizes) are a contributing factor.

#### Observable Trend 2:

Charter schools sginificantly outperform district schools in percentage of students passing math and reading. This is not onnly true in the aggregate (see "Schools by Score Type") but in terms of individual schools. The top five performing school in the district are all charter schools (see "Top Performing Schools") and the lowest performing school are all district schools (See "Bottom Performing Schools"). 

In this case, more analysis is needed to determine the reason for this finding. The charter schools in this district tend to be smaller (though not always the case). Qualitative data is likely needed as well, as other possible explanations include teacher performance, ciriculum, and the home life of the student population. The analysis here is not enough to determine the causes behind this finding. 
