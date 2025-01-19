# My Excel Data Analytics Projects

## 1. Data Jobs Salaries Dashboard

## 2. Data Skills and Salary Relationshp Analysis

## Introduction
As a job seeker I have always been curious to learn about what skills an applicant is expected to have for a certain position and how valued these skills are in the job market around the world. This 2023 dataset that includes jobs and requirements for each job came in handy for such analysis. 

### To help with our findings a list of questions will be very useful to outline the analysis process: 


1️⃣ Do more skills get you better pay?

2️⃣ What’s the salary for data jobs in different regions?

3️⃣ What are the top skills of data professionals?

4️⃣ What’s the pay for the top 10 skills?

### What skills were used in the project?

🖥️DAX

📊Pivot Tables

📈Pivot Charts

🔍Power Query 

🔄Power Pivot


### The Dataset


👨‍💼Job title

📍Job Location

💡Job skills

💸Job Salaries


## 1️⃣ Do more skills get you better pay?

🔍 Skill: Power Query (ETL)

📥 Extract
I used Power Query first of all to extract the original dataset and create two queries:
🗃️ First one with all the data jobs information.
🔧 The second breaking up each row containing all the skills by position into separate rows for each job ID.

🔄 Transform

Then I performed some transformation steps to each query:
- changed data types
- cleaned the text in certain columns
- added a month and year column
- added a column where hourly salary is multiplied by 2080(approx. work hours a year) to compare that to the yearly salary
- added index in order to connect the salary and skills queries in the future analysis
- created a separate Jobs skills query by referencing the original Jobs Salary query to analyse skill sets separately


Jobs Salary

![Screenshot 2025-01-19 200819](https://github.com/user-attachments/assets/a3c3634b-261e-42f1-99fe-3912b980d872)

Jobs Skills

![Screenshot 2025-01-19 210037](https://github.com/user-attachments/assets/18df208c-83c2-41af-94fd-e34e68246c64)

📩 Load

Subsequently, I loaded the dataset into the workbook.

Jobs salary Query


![Screenshot 2025-01-19 213409](https://github.com/user-attachments/assets/e12a371e-31c8-4042-a32e-21926f6ed6eb)

Jobs Skills Query

![Screenshot 2025-01-19 213422](https://github.com/user-attachments/assets/a7cf5eed-9126-4645-a088-246c0e0186a2)

📈Analysis

🟩 There is a positive correlation between the number of skills and median salary, thus the more skills the job requires the higher the remuneration. Also, the salary proves to be significantly higher in senior roles.

![Screenshot 2025-01-19 193650](https://github.com/user-attachments/assets/c50e810f-3ceb-46af-b996-f275d3a5fa15)


2️⃣ What’s the salary for data jobs in different regions?

🖥️ Skills: PivotTables & DAX
Pivot Table
🔢 I created a PivotTable using the Data Model I created with Power Pivot.
📊 I moved the job_title_short to the rows area and salary_year_avg into the values area.
🧮 Then I added new measure to calculate the median salary for United States jobs.

`=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States")`

🧮 DAX
To calculate the median year salary I used DAX.

`Median Salary := MEDIAN(data_jobs_all[salary_year_avg])`


📊 Analysis

- The most in demand positions both in the US and internationally are Machine Learning Engineer, Senior Data Engineer, Senior Data Scientist marking
- The difference in the Median Salaries between the US and other countries is evident especially in non-senior positions, indicating high demand and concentration of these jobs in the US.

![Screenshot 2025-01-19 221306](https://github.com/user-attachments/assets/06c88ab4-a14d-4786-aa69-a199d3a6833a)


![Screenshot 2025-01-19 221248](https://github.com/user-attachments/assets/d001d3d7-3c67-4d1c-b244-f32a09a764c5)


3️⃣ What are the top skills of data professionals?

🔄 Skill: Power Pivot

🔗 I created a data model by integrating the data_jobs_all and data_jobs_skills tables into one model.
🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.


