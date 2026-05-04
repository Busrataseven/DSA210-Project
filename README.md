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
* Model performance shows **almost no improvement after adding GDP**  
* The coefficient of GDP in Linear Regression is **very small**, indicating low predictive power  

This confirms that **macro-level economic indicators do not significantly contribute to salary prediction when job-related variables are already included**.

---

## Interpretation of Model Results

The results from EDA, hypothesis testing, and machine learning are highly consistent.

### Linear Regression Coefficients Insight

One interesting observation is that the coefficient for `skills_sql` appears negative. This does **not** mean that SQL reduces salary.

This occurs due to:

* **Multicollinearity**: Skill variables (Python, ML, SQL, cloud) overlap in many roles  
* **Role distribution**: SQL is commonly required in entry-level or analyst roles, which tend to have lower salaries  

Therefore, the negative coefficient reflects **dataset structure rather than a true negative effect**.

---

### Effect of GDP Enrichment

After adding GDP per capita:

* The overall structure of coefficients remains **largely unchanged**  
* Experience-related variables remain dominant  
* GDP has **minimal impact on predictions**

This suggests that salary variation is primarily driven by **individual and role-based factors**, not country-level economic differences.

---

## Conclusion

This project shows that salary in the AI and data science job market is primarily driven by **experience and structural job factors**.

* Both models achieve similar performance (**R² ≈ 0.56**)  
* Relationships in the dataset are mostly **linear**  
* GDP per capita adds **very limited predictive value**  

Overall, **career progression and job characteristics dominate salary outcomes**, while macroeconomic indicators play a minimal role in this dataset.

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
