AI and Data Science Job Market Analysis Factors Affecting Salaries
DSA210|Spring 2025–2026
Büşra Ataseven GitHub: Busrataseven/DSA210-Project
1. Motivation
The AI and data science job market has expanded rapidly in recent years, creating a wide variety of roles with significantly different compensation levels. Yet it remains unclear what actually drives these differences. Is it the technical skills a candidate holds? Their seniority? The size of the company? Or the economic conditions of the country they work in?
This project was motivated by a genuine interest in answering this question with data rather than intuition. With over 10,000 job postings available and the opportunity to enrich the dataset with World Bank macroeconomic indicators, this project applies the full data science pipeline — from exploration to machine learning — to identify what truly shapes salary in the AI job market.
Central research question: Are salaries primarily shaped by individual qualifications (experience, skills), or by external structural and economic factors (company size, country GDP)?
2. Data Source
Primary Dataset
• File: AI_Job_Market_Trends_2026.csv
• Source: Kaggle — "AI and Data Science Job Market 2025–2026"
• Size: 10,345 job postings, 19 variables
• No missing values — suitable for direct analysis without preprocessing
Key variables include:
Type
Variables
Categorical
job_title, company_size, company_industry, country, remote_type, experience_level, education_level, hiring_urgency
Numerical
salary, years_experience, job_openings
Binary (skills)
skills_python, skills_sql, skills_ml, skills_deep_learning, skills_cloud
Summary statistics show salary ranging from ~$45,000 to ~$204,000, with a mean of approximately $113,438 and a standard deviation of ~$31,389 — indicating substantial variation across roles.
Data Enrichment: World Bank GDP Per Capita
To extend the analysis beyond job-level variables, GDP per capita data (2023) was sourced from the World Bank (API_NY.GDP.PCAP.CD) and merged with the primary dataset on the country column.
• 2,944 entries had no GDP match and were filled with the median GDP to preserve dataset completeness
• This enrichment allowed investigation into whether country-level economic conditions contribute to salary prediction
3. Data Analysis
The analysis followed a structured three-stage pipeline.
3.1 Exploratory Data Analysis (EDA)
Salary Distribution The salary distribution is slightly right-skewed, with most salaries concentrated in a moderate range (~$89,000–$134,000 for the middle 50%) and a longer tail of high earners on the right. This is consistent with real-world tech compensation patterns where a smaller group of senior/specialized roles pulls the average upward.
Salary vs. Experience Level A boxplot of salary by experience level reveals a clear and consistent gradient: entry-level roles earn the least, followed by mid-level, then senior. The separation between groups is visually pronounced, suggesting experience is a strong predictor even before formal testing.
Salary vs. Work Type Boxplots for remote, hybrid, and onsite roles show heavily overlapping distributions with nearly identical medians. The bar chart of average salary by work type confirms this — all three types show similar mean compensation with no obvious separation.
Job Title, Company Size, and Country Distributions The dataset includes a diverse range of job titles with the top 10 covering roles such as AI Engineer, Machine Learning Engineer, Data Scientist, and Business Analyst. Company size is spread across Startup, MNC, and other categories. The top countries include Germany, Australia, and Canada, though the country distribution is uneven — some countries appear far more frequently than others, which is relevant to the GDP analysis.
GDP Per Capita Distribution The GDP distribution is highly right-skewed, with most countries clustered in a mid-range and a small number of high-GDP outliers. The correlation heatmap confirms that GDP per capita has nearly zero correlation with salary (r = 0.018), while years of experience shows a positive relationship and ML/cloud skills show moderate positive correlations.
3.2 Hypothesis Testing
Test 1 — ANOVA: Does experience level affect salary?
Value
Method
One-Way ANOVA
H₀
Mean salary is equal across all experience levels
F-statistic
3615.56
p-value
0.0
Result
✅ Reject H₀
The ANOVA result is decisive: with an F-statistic of 3615.56 and a p-value effectively equal to zero, there is an extremely strong and statistically significant difference in salary across experience levels. Experience level is a dominant salary driver.
Test 2 — T-test: Does work type affect salary?
Value
Method
Independent samples t-test (Remote vs. Onsite)
H₀
Remote and onsite salaries are equal
t-statistic
−0.46
p-value
0.645
Result
❌ Fail to reject H₀
With a p-value of 0.645 (far above the 0.05 threshold), there is no statistically significant difference between remote and onsite salaries. Work type does not independently influence salary.
3.3 Machine Learning
Features used: experience_level, years_experience, company_size, remote_type, education_level, skills_python, skills_sql, skills_ml, skills_deep_learning, skills_cloud
Train/test split: 80% training (8,276 samples) / 20% test (2,069 samples)
Model Results (without GDP)
Model
RMSE
R²
Linear Regression
20,900.96
0.5613
Random Forest
21,024.15
0.5561
Model Results (with GDP per Capita)
Model
RMSE
R²
Linear Regression + GDP
20,904.65
0.5611
Random Forest + GDP
20,710.22
0.5692
Both models perform similarly before and after adding GDP, confirming the near-zero correlation observed in EDA. The slight improvement in Random Forest with GDP (+0.013 R²) hints that GDP may introduce minor non-linear patterns, but the overall effect is negligible.
Linear Regression Coefficients (top features):
Feature
Coefficient
experience_level
+24,575
skills_deep_learning
+15,490
skills_ml
+14,749
skills_cloud
+9,900
skills_python
+556
education_level
+312
remote_type
+137
years_experience
−75
skills_sql
−201
company_size
−1,866
Why is skills_sql negative? This does not mean SQL reduces salary. In linear regression with multiple correlated predictors, multicollinearity can produce counterintuitive signs. SQL is also disproportionately required in entry-level analyst roles, which have lower average salaries. The negative coefficient reflects dataset structure and variable correlation, not a true causal negative effect.
Feature Importance (Random Forest): The top predictors by importance score are experience level, years of experience, and company size — all structural/career factors. Technical skills rank lower, indicating they function more as prerequisites than differentiators.
4. Findings
The EDA, hypothesis tests, and machine learning models all point to the same conclusion:
Salary in the AI and data science job market is primarily determined by career progression and structural job factors — not by individual technical skills or macroeconomic conditions.
Specific findings:
• Experience dominates. The ANOVA test (F = 3615, p ≈ 0) and Random Forest feature importance both confirm that experience level is the single strongest predictor of salary. Seniority matters more than any skill.
• Remote work carries no salary premium. Despite common belief, the t-test shows no significant salary difference between remote and onsite roles (p = 0.645). Where you work does not determine what you earn.
• Deep learning and ML skills add the most value among technical skills. With coefficients of +15,490 and +14,749 respectively, these advanced skills are the most financially rewarded — unlike general skills such as Python or SQL.
• GDP per capita has minimal predictive power. With a correlation of 0.018 and near-zero improvement in model R² after enrichment, country-level economic conditions do not meaningfully explain salary variation once job-level features are included.
• The data has a largely linear structure. The near-identical R² scores of Linear Regression (~0.561) and Random Forest (~0.556) without GDP confirm that a simple linear model captures the salary patterns almost as well as a complex ensemble — there are no significant non-linear interactions to exploit.
5. Limitations and Future Work
Limitations
• The analysis relies on a single Kaggle dataset; findings may not generalize to all industries, geographies, or time periods.
• Key real-world salary determinants are absent: negotiation outcomes, internal pay bands, cost of living, visa constraints, and company-specific compensation structures.
• R² ≈ 0.56 means approximately 44% of salary variance remains unexplained by available features.
• Skill variables exhibit multicollinearity, limiting the interpretability of individual linear coefficients.
• The dataset reflects job postings, not accepted salaries — posted ranges may not reflect actual offers.
• The country distribution is uneven, with some countries appearing far more frequently, which may bias GDP-related findings.
Future Work
• Incorporate cost of living indices alongside GDP for more nuanced geographic salary analysis
• Explore skill combinations rather than individual binary skill flags (e.g., does Python + cloud together command a premium?)
• Apply XGBoost or gradient boosting models to probe non-linear interactions more thoroughly
• Use longitudinal data to track how salary drivers evolve as the AI market matures
• Investigate interaction terms (e.g., does remote work affect senior vs. entry-level salaries differently?)
• Collect data on actual hired salaries rather than postings for more accurate modeling
6. Tools and Technologies
Category
Tools
Language
Python 3
Data manipulation
Pandas, NumPy
Visualization
Matplotlib, Seaborn
Statistical testing
SciPy
Machine learning
Scikit-learn
Environment
Jupyter Notebook
Version control
Git, GitHub
7. How to Reproduce
# Clone the repository
git clone https://github.com/Busrataseven/DSA210-Project.git
cd DSA210-Project
# Install dependencies
pip install -r requirements.txt
# Run notebooks in order:
# 1. EDA & Hypothesis Testing
jupyter notebook "AI_&_Data_Science_Job_Market_Analysis_Factors_Affecting_Salaries.ipynb"
# 2. Machine Learning
jupyter notebook ML_Analysis.ipynb
AI Usage Disclosure
AI tools (ChatGPT, Claude) were used during this project to support code debugging, improve report structure, and refine written explanations. Specific use cases included resolving errors in Pandas operations, improving the clarity of written interpretations, and getting feedback on report organization. All analyses, model implementations, results, and final interpretations were reviewed and verified manually by the author.
