AI & Data Science Job Market Analysis
Project Overview

This project analyzes the key factors affecting salaries in the AI and Data Science job market.

The aim is to understand how variables such as experience level, company size, and technical skills influence salary levels using data analysis, statistical testing, and basic machine learning models.

Dataset

The dataset contains 10,345 job postings with features such as:

Job Title
Company Size
Experience Level
Years of Experience
Salary
Country
Work Type (Remote / Hybrid / Onsite)
Technical Skills (Python, SQL, ML, etc.)

The dataset includes both categorical and numerical variables and does not contain missing values.

Methods
Exploratory Data Analysis (EDA)
Examined salary distribution
Analyzed relationships between salary and experience
Created visualizations using Seaborn and Matplotlib
Hypothesis Testing
ANOVA was used to test the effect of experience level on salary
T-test was used to test the effect of work type on salary
Machine Learning
Linear Regression was used as a baseline model
Random Forest Regressor was used to capture potential non-linear relationships

Models were evaluated using RMSE and R² scores.

Key Findings
Experience level has a strong and statistically significant effect on salary
Salaries increase with higher experience levels
Work type (remote, hybrid, onsite) does not have a significant impact on salary
Salary distribution is slightly right-skewed
Machine Learning Results
Both models showed similar performance (R² around 0.56)
Linear Regression performed slightly better than Random Forest
This suggests that the relationship between features and salary is mostly linear
Feature Importance

According to the Random Forest model:

Experience level is the most important factor
Followed by years of experience and company size

Technical skills such as Python, SQL, and cloud technologies have relatively lower importance compared to experience-related variables.

Interpretation

The machine learning results are consistent with the findings from EDA and hypothesis testing.

Overall, salary appears to be driven mainly by experience and structural factors rather than individual technical skills alone.

Limitations and Future Work

This analysis is based on a single dataset and does not include all possible factors affecting salary.

Possible improvements:

Including external data such as cost of living or economic indicators
Trying more advanced models
Performing deeper analysis on skill combinations
Tools Used
Python
Pandas
NumPy
Seaborn
Matplotlib
Scikit-learn
