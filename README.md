# Overview
Welcome to my analysis of the data job market, focusing on data analyst roles. This project was created out of a desire to navigate and understand the job market more effectively. It delves into the top-paying and in-demand skills to help find optimal job opportunities for data Engineers.

The data sourced from Luke Barousse's Python Course which provides a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python scripts, I explore key questions such as the most demanded skills, salary trends, and the intersection of demand and salary in data analytics.

## The Questions
Below are the questions I want to answer in my project:

What are the skills most in demand for the top 3 most popular data roles?
How are in-demand skills trending for Data Engineers?
How well do jobs and skills pay for Data Engineers?
What are the optimal skills for data Engineers to learn? (High Demand AND High Paying)
Tools I Used
For my deep dive into the data analyst job market, I harnessed the power of several key tools:

- Python: The backbone of my analysis, allowing me to analyze the data and find critical insights.I also used the following Python libraries:
- Pandas Library: This was used to analyze the data.
- Matplotlib Library: I visualized the data.
- Seaborn Library: Helped me create more advanced visuals.
- Jupyter Notebooks: The tool I used to run my Python scripts which let me easily include my notes and analysis.
- Visual Studio Code: My go-to for executing my Python scripts.
- Git & GitHub: Essential for version control and sharing my Python code and analysis, ensuring collaboration and project tracking.

# Data Preparation and Cleanup
This section outlines the steps taken to prepare the data for analysis, ensuring accuracy and usability.

## Import & Clean Up Data
I start by importing necessary libraries and loading the dataset, followed by initial data cleaning tasks to ensure data quality.

``` python

# Importing Libraries
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt  

# Loading Data
dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

# Data Cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)

```

## Filter US Jobs
To focus my analysis on the U.S. job market, I apply filters to the dataset, narrowing down to roles based in the United States.

``` python

df_US = df[df['job_country'] == 'United States']


```


# Data Job Market Analysis 📊

## This project analyzes the data job market, identifying top roles, in-demand skills, and key trends from real job postings.

### Top Skills for Popular Data Roles

Focused on the 3 most popular data roles

Extracted the top 5 skills for each role based on job postings

Helps you identify which skills to prioritize depending on your target role

📂 Notebook: [2_Skill_Demand.ipynb](4_Project\2_Skill_Demand.ipynb)

#Visualization Highlights

Bar plots show the top skills for each role

Bars represent the percentage of postings requiring each skill

Consistent scales and labels make comparisons easy

# Example snippet

```
fig, ax = plt.subplots(len(job_titles), 1)


for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)[::-1]
    bars = sns.barplot(
        data=df_plot,
        x="skill_percentage",
        y="job_skills",
        ax=ax[i],
        hue="job_skills",         
        palette="viridis",
        dodge=False,
        legend=False              
    )

fig.suptitle("Percentage of Job Postings Requiring Each Skill", fontsize=16, fontweight="bold")



plt.show()

```

### Results

![Visualization of Top Skills for Data Nerds](4_Project\images\skill_demand.png)

## Quick insights into high-demand skills across roles.

- SQL is the most requested skill for Data Engineers and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.

- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Engineers and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).

-  Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).


# The Analysis
## 2. How are in demand skills trending for Data Engineering?

### Visualize Data

``` python

from matplotlib.ticker import PercentFormatter
sns.lineplot(data=df_plot, dashes=False, linewidth=2.2, markers=True, legend=False)

# Set y-axis to percentage format
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))
plt.show()

```
## Results
![Trending Top skills for Data Engineers in the US](4_Project\images\skills_trend.png)
*Visualizing the trending top skills for Data Engineers in US for 2023.*

## Insights:

- SQL dominates 🏆 → Always the top skill (~65–70%), showing that it’s the most essential for data engineering roles in the US.

- Python is consistently second 🐍 → Ranges between 60–67%, proving it’s nearly as important as SQL, with only slight seasonal dips (lowest in September).

- Cloud skills (AWS & Azure) are strong ☁️ → AWS stays higher (~40–46%) than Azure (~30–34%), but Azure shows a late-year spike in October–December.

- Spark holds steady 🔥 → Around ~30–34%, with small dips mid-year but rebounds by November, showing it’s a stable demand skill.



# The Analysis
## 4. What is the most optimal skills to learn for Data Engineer ?

``` python

from adjustText import adjust_text
import matplotlib.pyplot as plt

plt.scatter(df_DA_skills_high_demand['skill_percent'], df_DA_skills_high_demand['median_salary'])
plt.show()

```

![Most Optimal Skills for Data Engineer in US](4_Project\images\optimal_using_matplot.png)

# Modification Using SeaBorn

![Most Optimal Skills for Data Engineer in US](4_Project\images\optimal_using_seaborn.png)

## Insights

### Here are the key insights from this scatter plot 📊:

- SQL & Python dominate in demand → SQL (~70%) and Python (~55%) are required in most data analyst jobs, but they offer relatively lower median salaries ($125K–$128K).

- High-paying but niche skills → Kafka ($145K), Scala ($140K), and NoSQL (~$140K) provide the highest salaries but appear in less than 20% of jobs.

- Cloud tools vary → AWS (~45% jobs, $132K) has stronger demand and decent salary, while Azure (~30% jobs, $125K) is less demanded and lower paid.

- Balanced skills → Spark (~35% jobs, $138K) and Java (~25% jobs, $137K) sit in the middle—good mix of demand and salary.

- Snowflake & Hadoop → Moderate demand (~25–30%) but pay around $130–132K, making them solid but not standout skills.

👉 Overall: SQL & Python are must-learns for entry, but specialized skills like Kafka, Scala, and NoSQL give the best salary boost if you want to differentiate yourself


# What I Learned

Throughout this project, I deepened my understanding of the data analyst job market and enhanced my technical skills in Python, especially in data manipulation and visualization. Here are a few specific things I learned:

- **Advanced Python Usage**: Utilizing libraries such as Pandas for data manipulation, Seaborn and Matplotlib for data visualization, and other libraries helped me perform complex data analysis tasks more efficiently.
- **Data Cleaning Importance**: I learned that thorough data cleaning and preparation are crucial before any analysis can be conducted, ensuring the accuracy of insights derived from the data.
- **Strategic Skill Analysis**: The project emphasized the importance of aligning one's skills with market demand. Understanding the relationship between skill demand, salary, and job availability allows for more strategic career planning in the tech industry.

## Insights
This project provided several general insights into the data job market for analysts:

- **Skill Demand and Salary Correlation**: There is a clear correlation between the demand for specific skills and the salaries these skills command. Advanced and specialized skills like Python and Oracle often lead to higher salaries.
- **Market Trends**: There are changing trends in skill demand, highlighting the dynamic nature of the data job market. Keeping up with these trends is essential for career growth in data analytics.
- **Economic Value of Skills**: Understanding which skills are both in-demand and well-compensated can guide data analysts in prioritizing learning to maximize their economic returns.

# Challenges I Faced
This project was not without its challenges, but it provided good learning opportunities:

- **Data Inconsistencies**: Handling missing or inconsistent data entries requires careful consideration and thorough data-cleaning techniques to ensure the integrity of the analysis.
- **Complex Data Visualization**: Designing effective visual representations of complex datasets was challenging but critical for conveying insights clearly and compellingly.
- **Balancing Breadth and Depth**: Deciding how deeply to dive into each analysis while maintaining a broad overview of the data landscape required constant balancing to ensure comprehensive coverage without getting lost in details.


## Conclusion
This exploration into the data analyst job market has been incredibly informative, highlighting the critical skills and trends that shape this evolving field. The insights I got enhance my understanding and provide actionable guidance for anyone looking to advance their career in data analytics. As the market continues to change, ongoing analysis will be essential to stay ahead in data analytics. This project is a good foundation for future explorations and underscores the importance of continuous learning and adaptation in the data field.