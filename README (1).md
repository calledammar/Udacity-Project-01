# Developer Salary Prediction (Stack Overflow Survey)

Predict a developer’s annual income from Stack Overflow Developer Survey responses using a clean, reproducible CRISP‑DM workflow. This repo includes a well‑documented notebook, business questions with answers and visuals, and feature‑importance analysis with SHAP before model testing.

## Motivation
Compensation varies widely across countries, roles, and experience. The aim is to (1) explore what most strongly influences salary and (2) build a baseline model that estimates individual compensation while remaining transparent about the drivers behind the predictions.

## Repository Structure
```
.
├── README.md                # You’re here
├── BLOG_POST.md             # Non‑technical summary (200–500 words)
├── Udacity_Project.ipynb    # Main notebook (EDA → prep → SHAP → model → eval)
└── images/
    └── cover.png            # Blog/README cover image
```
> If your notebook file name differs (e.g., `Udacity_Project_enhanced.ipynb`), update the tree above accordingly.

## Data
- **Source:** Stack Overflow Developer Survey (CSV). Download from the official survey site and place the file locally (not committed to the repo).
- **Target:** `ConvertedCompYearly` (annual compensation).
- **High‑level cleaning:** filter missing target; harmonize years‑of‑experience fields; expand or drop multi‑select columns when useful; cap extreme outliers for stable training and plots.

## Environment & Libraries
Tested with Python 3.9+
- Core: `pandas`, `numpy`, `matplotlib`, `seaborn`
- Modeling: `scikit-learn` (RandomForestRegressor, pipelines)
- Optional: `xgboost`, `catboost`

> Tip: create a virtual env, then `pip install -r requirements.txt` (include the packages above).

## How to Run
1) Clone the repo and create a virtual environment.  
2) Install requirements.  
3) Open the notebook and run all cells top‑to‑bottom.

```
jupyter notebook Udacity_Project.ipynb
```

## CRISP‑DM Overview
1. **Business Understanding** – Estimate developer salary and understand key drivers.  
2. **Data Understanding** – EDA of distributions, missingness, and relationships (e.g., salary vs. experience, company size).  
3. **Data Preparation** – Clean target, engineer experience fields, one‑hot encode categoricals, split train/test.
4. **Exploratory Questions and Answers** - Before building predictive models, it's important to explore the cleaned data and answer business-oriented questions that provide context. Here we pose several questions and answer them using visualizations and summary statistics.
5. **Modeling** – Random Forest (trees don’t require scaling); hyperparameters set for stability.  
6. **Evaluation** – Report MAE/MSE/R² on the test set.  
7. **Conclusion** - Final Concusions and reccomendations

## Exploratory Questions (asked & answered in the notebook)
1. **How is compensation distributed?** (Right‑skewed; long tail; use hist/boxplot; winsorize/cap for clarity.)  
2. **What is the relationship between years of professional experience and salary?** (Positive, diminishing marginal gains at higher experience.)  
3. **Does working remotely relate to higher compensation?** (Patterns differ by country; remote status interacts with geography and role.)  
4. **How does company size relate to pay?** (Mid‑to‑large orgs often pay more; inspect by region.)  
5. **Which self‑reported traits show the strongest association with salary?** (SHAP ranks features—commonly years of professional coding, country/region, company size, role, education.)

## Results (summary)
- A baseline Random Forest performs competitively for tabular survey data (see MAE/R² in the notebook).  
- **Top drivers (SHAP):** years of professional coding, country/region, company size, role, and education typically dominate.  
- Findings should be interpreted cautiously due to self‑reporting and regional mix.

## Acknowledgments
- Stack Overflow – Developer Survey data.  
- Open‑source libraries: pandas, numpy, matplotlib, seaborn, scikit‑learn, shap, catboost, xgboost.
