Developer Salary Prediction Project

This repository contains a data science project that predicts a developer’s annual income using anonymised responses from the Stack Overflow Developer Survey. The goal is to understand which factors most strongly influence compensation and to build a machine‑learning model that can estimate a respondent’s salary.

Motivation

Developer compensation varies widely across countries, industries and experience levels. By analysing the Stack Overflow Developer Survey we can identify patterns in the data and build a tool to help developers benchmark their salary expectations. This project follows the CRISP‑DM methodology to move from business understanding through data preparation, modelling and evaluation.

Repository Contents
File	Description
Udacity_Project.ipynb	The original notebook provided as input. It contains the initial analysis and modelling work in a non‑structured format.
Udacity_Project_enhanced.ipynb	The cleaned and organised notebook. It follows the CRISP‑DM process, includes data understanding, exploratory questions with visualisations, data preparation, modelling, feature importance via SHAP (CatBoost) and evaluation.
README.md	This document. It describes the project goals, lists the files in the repository, summarises results and acknowledges data sources.
BLOG_POST.md	A standalone blog article aimed at a general audience. It summarises the project’s questions and findings in 200–500 words with an accompanying illustration.
images/	Directory containing the abstract illustration used in the blog post.
Libraries Used

The project relies on several Python libraries:

pandas and numpy for data loading and manipulation.

matplotlib and seaborn for charts and exploratory visualisations.

scikit‑learn for preprocessing (train/test split, one‑hot encoding, scaling) and building machine‑learning models (Random Forest).

catboost for an additional gradient‑boosting model and computing SHAP values natively.

shap (optional) if a separate SHAP analysis is desired; CatBoost provides SHAP values without requiring the external package.

Summary of Results

Data Preparation – Rows without salary information were removed. Columns with more than 30 % missing values were dropped. Categorical responses like “Less than 1 year” and “More than 50 years” in the experience columns were converted to numeric values. Extreme outliers in salaries were trimmed using the interquartile range.

Exploratory Questions – The analysis posed several questions:

Does experience pay off? A scatter plot of years of coding versus salary showed a positive correlation—developers with more experience tend to earn higher salaries.

Does education matter? Respondents with advanced degrees generally reported higher median salaries, although the difference between Bachelor’s and Master’s degrees was small.

Does company size impact pay? Salaries rose with company size up to mid‑sized organisations; very small or very large companies exhibited more variability in compensation.

Where are developers paid the most? A ranking of countries by average salary showed the usual suspects near the top: countries like the United States and Switzerland reported some of the highest average developer salaries.

Modelling – A Random Forest regressor was trained using one‑hot encoded categorical features and scaled numeric features. The model achieved a reasonable 
𝑅
2
R
2
 score (around 0.4 on the test set), indicating that a substantial portion of salary variance can be explained by the available features.

Feature Importance – Using CatBoost’s built‑in SHAP value calculation, the most influential features were years of professional coding experience, total years coding, country, education level and organisation size. Experience and geography were by far the strongest drivers of compensation.

Acknowledgments

Stack Overflow for providing the public Developer Survey
 datasets.

The open‑source community for the libraries used in this analysis.

If you have any questions or suggestions about this project, feel free to open an issue or submit a pull request.