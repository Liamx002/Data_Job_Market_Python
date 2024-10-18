# The Analysis

## 1. What are the most demanded skills for the 3 most popular data roles?

In order to discover the in demand skills for the top 3 most popular data roles, I filtered out the three most popular data roles and then found the top 5 in demand skills that correspond to each given role. This means the quiery effectively highlights the most popular job titles and their respective most popular skills, showing the skills I should pay attention to depending on the the role I'm focussing on.

 View the notebook with the steps included here: [2_Skills_Demand](3_Project\2_Skills_Demand.ipynb)

 ### Labelling the Visualisation

 ```Python
 for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc["job_title_short"] == job_title].head(5)
    
    sns.set_theme(style="ticks")
    sns.barplot(data=df_plot, x="skill_percent", y="job_skills", ax=ax[i], hue="skill_count", palette="dark:b_r")
    
    ax[i].set_xlim(0, 78)
    ax[i].set_title(job_title)
    ax[i].set_ylabel("")
    ax[i].set_xlabel("")
    ax[i].get_legend().remove()
    for j in range(len(df_plot)):
        ax[i].text(df_plot["skill_percent"].iloc[j],
                   df_plot["job_skills"].iloc[j],
                   f'{int(df_plot["skill_percent"].iloc[j]):.0f}%',
                   va="center")
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])
```

### Results 

![Visualisation of Top Skills for each Data Role](3_Project\Images\proportion_top_skills_job_roles.png)

### Insights

1. Python and SQL are skills that are highly valued within all three job roles.

2. Python is found in required skills nearly three quaters of the time, making it an essential skill within this job role.

3. Data Analyst Roles posses a more even proportioned spread of skills within their job postings while both Data Engineers and Data Scientists have very strongly weighted skills comparitive to much lower requested skills. 