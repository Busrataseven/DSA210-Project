# AI and Data Science Job Market Analysis

## Project Overview

This project investigates the key factors influencing salaries in the AI and Data Science job market.

With the rapid growth of AI-related roles, understanding what truly drives salary differences has become increasingly important. This study aims to identify whether salary is primarily shaped by **individual qualifications (skills, experience)** or **external factors (company structure, economic conditions)**.

To achieve this, the project combines **exploratory data analysis (EDA)**, **statistical hypothesis testing**, and **machine learning models**.

---

## Dataset

The dataset contains **10,345 job postings** and includes both categorical and numerical variables such as:

* Job title
* Company size
* Experience level
* Years of experience
* Salary
* Country
* Work type (remote, hybrid, onsite)
* Technical skills (Python, SQL, ML, cloud, etc.)

The dataset is clean and does not contain missing values, making it suitable for direct analysis.

---

## Methodology

### Exploratory Data Analysis (EDA)

* Examined salary distribution
* Analyzed how salary varies across experience levels
* Visualized patterns using Seaborn and Matplotlib

### Hypothesis Testing

* **ANOVA test** to evaluate the impact of experience level on salary
* **T-test** to examine whether work type affects salary

### Machine Learning

* **Linear Regression** used as a baseline model
* **Random Forest Regressor** used to capture potential non-linear relationships

Models were evaluated using:

* RMSE (Root Mean Squared Error)
* R² (Coefficient of Determination)

---

## Key Findings

### Salary Drivers

* Experience level has a **strong and statistically significant effect** on salary
* Salaries increase consistently with higher experience levels
* Work type (remote, hybrid, onsite) does **not significantly affect salary**
* Salary distribution is slightly **right-skewed**, indicating a small group of high earners

---

### Machine Learning Results

* Both models performed similarly (**R² ≈ 0.56**)
* Linear Regression slightly outperformed Random Forest
* This suggests that salary relationships are largely **linear rather than complex or non-linear**

---

### Feature Importance

According to the Random Forest model:

* **Experience level** is the most influential factor
* Followed by **years of experience** and **company size**
* Technical skills (Python, SQL, cloud) have **lower relative importance**

This indicates that **career progression and seniority outweigh individual skill sets** in salary determination.

---

## Data Enrichment (GDP Analysis)

To extend the analysis, GDP per capita data was integrated as an external feature.

* The correlation between GDP per capita and salary is **extremely weak (~0.018)**
* This indicates **virtually no direct relationship** between national economic conditions and salary in this dataset

This finding suggests that **AI/Data Science salaries are largely driven by job-specific factors rather than macroeconomic conditions**.

---

## Interpretation

The results from EDA, hypothesis testing, and machine learning are highly consistent.

Overall, salary in the AI job market is primarily driven by:

* Experience and seniority
* Structural factors (company size, role hierarchy)

rather than:

* Individual technical skills alone
* Country-level economic conditions

---

## Limitations and Future Work

This study has several limitations:

* Based on a single dataset
* Does not include factors such as negotiation power, company-specific policies, or real-time market dynamics

Future improvements may include:

* Adding cost of living and economic indicators
* Applying more advanced machine learning models
* Analyzing combinations of technical skills in more depth

---

## Tools Used

* Python
* Pandas
* NumPy
* Seaborn
* Matplotlib
* Scikit-learn
