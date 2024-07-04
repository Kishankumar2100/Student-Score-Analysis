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
