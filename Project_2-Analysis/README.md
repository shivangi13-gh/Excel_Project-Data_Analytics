# Project 2 Analysis

## Introduction
To better understand the data job market, I analyzed salaries and skill requirements across various roles. The goal was to identify patterns in compensation and the skills that lead to higher-paying opportunities.

### Questions to Analyze
To understand the data science job market, I asked the following:
1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used
The following Excel skills were utilized for analysis:
- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Data Jobs Dataset
The dataset used for this project contains real-world data science job information from 2023. The dataset is available in the Excel course, which provides a foundation for analyzing data using Excel. 
It includes detailed information on:
- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

## 1️⃣ Do more skills get you better pay?
### 🔍 Skill: Power Query (ETL)
#### 📥 Extract
- I first used Power Query to extract the original data (`data_jobs_salary_all.xlsx`) and create two queries:
    - 🗃️ First one with all the data jobs information.
    - 🔧 The second listing the skills for each job ID.

#### 🔄 Transform
- Then, I transformed each query by changing column types, removing unnecessary columns, cleaning text to eliminate specific words, and trimming excess whitespace.
    - 📊 data_jobs_salary

      ![2_data_jobs_salary_all](https://github.com/user-attachments/assets/34bd553c-b5de-4198-9012-d1b92cd09d2a)
  
    - 🛠️ data_job_skills

      ![2_data_job_skills](https://github.com/user-attachments/assets/aef947e7-7216-43c1-9c1e-aa88a04aba02)
        
#### 🔗 Load
- Finally, I loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
    - 📊 data_jobs_salary

        ![2_data_jobs_salary_all_pq](https://github.com/user-attachments/assets/0dfcdfec-3969-4602-a939-d292e2b1415d)

    - 🛠️ data_job_skills

       ![2_data_job_skills_pq](https://github.com/user-attachments/assets/12986a4e-216d-4f07-a7d1-854da28052c3)
 
### 📊 Analysis
#### 💡 Insights
- 📈 There is a positive correlation between the number of skills requested in job postings and the median salary, particularly in roles like Senior Data Engineer and Data Scientist.
- 💼 Roles that require fewer skills, like Business Analyst, tend to offer lower salaries, suggesting that more specialized skill sets command higher market value.

    ![Salary_vs_Skills](https://github.com/user-attachments/assets/fb69784c-69d8-4bf2-98f4-161fd7b4228a)

#### 🤔 So What
- This trend emphasizes the value of acquiring multiple relevant skills, particularly for individuals aiming for higher-paying roles.

## 2️⃣ What’s the salary for data jobs in different regions?
### 🧮 Skills: PivotTables & DAX
#### 📈Pivot Table
- 🔢 I created a PivotTable using the Data Model I created with Power Pivot.
- 📊 I moved the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- 🧮 Then I added new measure to calculate the median salary for United States jobs.
    ```
    =CALCULATE(
        MEDIAN(data_jobs_salary[salary_year_avg]),
        data_jobs_salary[job_country] = "United States")
    ```

#### 🧮 DAX
- To calculate the median year salary I used DAX.
    ```
    Median Salary := MEDIAN(data_jobs_salary[salary_year_avg])
    ```

### 📊 Analysis
#### 💡 Insights
- 💼 Job roles like Senior Data Engineer and Data Scientist command higher median salaries both in the US and internationally, showcasing the global demand for high-level data expertise.
- 💰 The salary disparity between US and Non-US roles is particularly notable in high-tech jobs, which might be influenced by the concentration of tech industries in the US.

   ![Salary_Analysis](https://github.com/user-attachments/assets/6be91a14-a3cf-4842-949f-f4157c88cb79)
 
#### **🤔 So What**
- These salary insights are important for planning and salary negotiations, helping professionals and companies align their offers with market standards while considering geographical variations.

## 3️⃣ What are the top skills of data professionals?
### 🔧 Skill: Power Pivot
#### 💪 Power Pivot
- 🔗 I created a data model by integrating the `data_jobs_salary` and `data_jobs_skills` tables into one model.
- 🧹 Since I had already cleaned the data using Power Query; Power Pivot created a relationship between these two tables.

#### 🔗 Data Model
- I created a relationship between my two tables using the `job_id` column.

    ![2_relationship](https://github.com/user-attachments/assets/378b4285-1340-40fa-8a21-5ef8850518c3)

#### 📃 Power Pivot Menu
- The Power Pivot menu was used to refine my data model and makes it easy to create measures.

    ![2_pivot_menu](https://github.com/user-attachments/assets/4584a676-8147-40c5-b9eb-451f6b5f13c7)

### 📊Analysis
#### 💡Insights
- 💻 SQL and Python dominate as top skills in data-related jobs, reflecting their foundational role in data processing and analysis.
- ☁️ Emerging technologies like AWS and Azure also show significant presence, underlining the industry's shift towards cloud services and big data technologies.

   ![Skill_Job_Analysis](https://github.com/user-attachments/assets/6881d464-73c6-42c0-baf0-e55857ea0fef)
 
#### 🤔So What
- Understanding prevalent skills in the industry not only helps professionals stay competitive but also guides training and educational programs to focus on the most impactful technologies.

## 4️⃣ What’s the pay of the top 10 skills?
### 📊 Skill: Advanced Charts (Pivot Chart)
#### 📈 PivotChart
- I created a combo PivotChart to plot median salary and skill likelihood (%) from my PivotTable.
    - 🪙 **Primary Axis:** Median Salary (as a Clustered Column)
    - 👍 **Secondary Axis:** Skill Likelihood (as a Line with Markers)
- To customize the chart, I added a title axis title, removed the lines (skill likelihood), and changed the markers to diamonds.

### 📊 Analysis
#### 💡Insights
- 💰 Higher median salaries are associated with skills like Python, Oracle, and SQL, suggesting their critical role in high-paying tech jobs.
- 📉 Skills like PowerPoint and Word have the lowest median salaries and likelihood, indicating less specialization and demand in high-salary sectors.

    ![Skill_Salary_Analysis](https://github.com/user-attachments/assets/adfe6de5-aedb-4cec-9cbf-269aba1c0a2b)

### 🤔So What
- This chart highlights the importance of investing time in learning high-value skills like Python and SQL, which are evidently tied to higher paying roles, especially for those looking to maximize their salary in the tech industry.

## Conclusion
As a data enthusiast, I embarked on this Excel-based project to uncover valuable insights about the data science job market. Using a dataset I've curated from real-world job postings, I analyzed job titles, salaries, locations, and essential skills. By leveraging Excel features like Power Query, PivotTables, DAX, and charts, I discovered key correlations between multiple skills and higher salaries, particularly in Python, SQL, and cloud technologies. 
I hope this project serves as a practical guide for data professionals and provides an overview of the skills needed for higher-paying roles.
