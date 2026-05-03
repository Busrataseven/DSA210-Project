# AI and Data Science Job Market Analysis

## Project Overview
This project analyzes the key factors affecting salaries in the AI and data science job market.

The aim is to understand how variables such as experience level, company size, and technical skills influence salary levels using data analysis, statistical testing, and basic machine learning models.

---

## Dataset
The dataset contains 10,345 job postings with the following features:

- Job title  
- Company size  
- Experience level  
- Years of experience  
- Salary  
- Country  
- Work type (remote, hybrid, onsite)  
- Technical skills (Python, SQL, ML, etc.)

The dataset includes both categorical and numerical variables and does not contain missing values.

---

## Methods

### Exploratory Data Analysis
- Examined salary distribution  
- Analyzed relationships between salary and experience  
- Created visualizations using Seaborn and Matplotlib  

### Hypothesis Testing
- ANOVA was used to test the effect of experience level on salary  
- T-test was used to test the effect of work type on salary  

### Machine Learning
- Linear regression was used as a baseline model  
- Random forest regressor was used to capture potential non-linear relationships  

Models were evaluated using RMSE and R² scores.

---

## Key Findings

- Experience level has a strong and statistically significant effect on salary  
- Salaries increase with higher experience levels  
- Work type (remote, hybrid, onsite) does not have a significant impact on salary  
- Salary distribution is slightly right-skewed  

### Machine Learning Results
- Both models showed similar performance (R² ≈ 0.56)  
- Linear regression performed slightly better than random forest  
- This suggests that the relationship between features and salary is mostly linear  

### Feature Importance
According to the random forest model:

- Experience level is the most important factor  
- Followed by years of experience and company size  

Technical skills such as Python, SQL, and cloud technologies have relatively lower importance compared to experience-related variables.

---

## Interpretation
The machine learning results are consistent with the findings from EDA and hypothesis testing.

Overall, salary appears to be driven mainly by experience and structural factors rather than individual technical skills alone.

---

## Limitations and Future Work
This analysis is based on a single dataset and does not include all possible factors affecting salary.

Possible improvements:
- Including external data such as cost of living or economic indicators  
- Trying more advanced models  
- Performing deeper analysis on skill combinations  

---

## Tools Used
- Python  
- Pandas  
- NumPy  
- Seaborn  
- Matplotlib  
- Scikit-learn  
