# Student Performance Analysis

This repository contains an analysis of student performance based on various factors such as demographics, parental background, study habits, and participation in extracurricular activities.

## Data Overview

The analysis is conducted using a dataset (`Expanded_data_with_more_features.csv`) containing information on student scores, demographics, and other relevant attributes.

### Initial Data Preparation

```python
import pandas as pd

# Load the dataset
df = pd.read_csv("Expanded_data_with_more_features.csv")

# Drop Unnamed Column
df.drop(columns=['Unnamed: 0'], inplace=True)

# Mapping Weekly Study Hours
df["WklyStudyHours"] = df["WklyStudyHours"].str.replace("05-Oct", "5-10")

# Visual Analysis

## Gender Distribution

From the chart, it is observed that the number of females in the dataset is higher than the number of males.

## Impact of Parent's Education on Student Scores

The heatmap illustrates a positive relationship between parent's education level and student scores.

## Impact of Parent's Marital Status on Student Score

From the analysis, there appears to be no significant impact on student scores due to their parent's marital status.

## Test Preparation Program Effectiveness

The chart below indicates that students who participated in the test preparation program generally achieved higher average scores in Math, Reading, and Writing compared to those who did not participate. This suggests that the test preparation program is effective in enhancing academic performance.

## Impact of Sports Participation on Academic Performance

Sports participation positively impacts academic performance. Students who engage in regular or occasional sports activities tend to achieve higher scores in Math, Reading, and Writing.

## Distribution of Ethnic Groups

The pie chart shows the distribution of students across different ethnic groups in the dataset.

## Weekly Study Hours and Total Score Analysis

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Calculate the average total score and count for each category of weekly study hours
avg_scores = df.groupby('WklyStudyHoursNum')['TotalScore'].agg(['mean', 'count']).reset_index()

# Plotting the bar plot
plt.figure(figsize=(10, 6))
sns.barplot(x='WklyStudyHoursNum', y='mean', data=avg_scores, palette='viridis')
plt.title('Average Total Score and Count by Weekly Study Hours')
plt.xlabel('Weekly Study Hours')
plt.ylabel('Average Total Score')
plt.grid(True)

# Annotate bars with count information
for index, row in avg_scores.iterrows():
    plt.text(index, row['mean'] + 1, f'n={row["count"]}', ha='center', color='black')

plt.savefig('weekly_study_hours_analysis.png')
plt.show()
