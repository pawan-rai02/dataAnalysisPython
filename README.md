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