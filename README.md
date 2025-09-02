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

- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of job postings.

- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).

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