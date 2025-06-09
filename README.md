# Global Education Analysis: Key Predictors of Adult Literacy  
**Author**: Sanjay DV

---

## Project Overview

This project conducts a comprehensive analysis of global education and socio-economic data to identify the key factors that influence adult literacy rates across different nations. The analysis begins with an exploratory look at historical trends and gender disparities, then proceeds to build and evaluate multiple regression models to uncover the most significant predictors of literacy.

A core focus of this project is diagnosing and addressing the statistical challenge of **multicollinearity**, demonstrating a robust and methodologically sound approach to inferential modeling.

---

## The Social & Economic Context

Understanding the drivers of literacy is fundamental to addressing global inequality and fostering economic development. High literacy rates are strongly correlated with:

- Improved health outcomes
- Greater economic opportunities
- More stable societies

For policymakers, NGOs, and international bodies like UNESCO, identifying the most impactful areas for investment is critical.

> **Key Question**: Which socio-economic and educational indicators have the most significant impact on a nation's adult literacy rate?

---

## About the Dataset

The analysis uses a comprehensive dataset of global socio-economic and educational indicators, compiled from sources such as the **World Bank**. The dataset covers multiple countries over several decades (primarily **1960–2014**) and includes:
The dataset can be accessed from this drive link I have created : https://drive.google.com/drive/folders/1VB2rQHypdtWVA4J_SG3cMPFGKTna9Mkb?usp=drive_link

- **Dependent Variable**:
  - Adult Literacy Rate (%)
  
- **Predictor Variables**:
  - GDP per capita
  - Fertility rate
  - Primary & Secondary school enrollment rates
  - Government expenditure on education
  - Internet/mobile/telephone usage
  - Pupil-teacher ratios
  - Life expectancy
  - ... and more

This dataset’s richness allows for in-depth exploration, but also introduces challenges like **high correlation between predictors**.

---

## Tech Stack

- **Data Analysis & Manipulation**: Pandas, NumPy  
- **Statistical Modeling**: Statsmodels (OLS, VIF), Scikit-learn (Ridge, Lasso, Gradient Boosting)  
- **Data Visualization**: Matplotlib, Seaborn  
- **Development Environment**: Jupyter Notebook, Python 3

---

## Methodology: A Story of Model Refinement

The modeling approach is structured to build interpretability and robustness through a series of refinements.

---

### Step 1: Exploratory Data Analysis (EDA)

- **Global Literacy Trends**: Literacy rates have steadily increased since the 1960s.
- **Gender Gap Analysis**: A persistent but narrowing gap between male and female literacy.
- **India Case Study**: Confirms the global trend of a shrinking gender gap in education access.

---

### Step 2: Baseline Modeling with OLS Regression

- **Initial Model**: High R-squared of 0.933 suggests strong explanatory power.
- **Issue Identified**: Severe **multicollinearity** found via **Variance Inflation Factor (VIF)**:
  - Life Expectancy VIF: 305
  - Net Enrollment Rate VIF: 292

> These extreme VIF values indicated unstable and misleading coefficients, necessitating a more robust approach.

---

### Step 3: Addressing Multicollinearity

#### Regularized Regression

- **Ridge Regression (L2)**:
  - Shrinks all coefficients to reduce variance
  - Effective at controlling multicollinearity, but retains all features

- **Lasso Regression (L1)**:
  - Shrinks some coefficients to zero
  - Performs **automatic feature selection**
  - Resulted in a simpler, more interpretable model

#### Ensemble Models

- **Random Forest & Gradient Boosting**:
  - Tree-based models inherently resistant to multicollinearity
  - Capture complex interactions without relying on linear assumptions

> **Gradient Boosting** emerged as the top performer, with R-squared = **0.936** and lower Mean Squared Error.

---

## Key Predictors of Literacy

Across robust models like **Lasso, Random Forest, and Gradient Boosting**, the following variables consistently emerged as most influential:

| Feature                         | Relationship        | Insight |
|--------------------------------|---------------------|---------|
| Net Enrollment Rate (Primary)  | Strong Positive     | Foundational education is crucial |
| Fertility Rate                 | Strong Negative     | Higher birth rates → lower literacy |
| Fixed Telephone Subscriptions  | Strong Positive     | Proxy for infrastructure and stability |
| Net Enrollment Rate (Secondary)| Positive            | Continued education also matters |

---

## Conclusion & Takeaways

This project successfully identifies **primary drivers of adult literacy** while navigating a highly correlated socio-economic dataset.

### Methodological Insight:
- A high R-squared doesn’t always mean a good model.
- Diagnostic tools like **VIF** are essential.
- Techniques like **Lasso Regression** and **Gradient Boosting** help mitigate multicollinearity and improve reliability.

### Policy Implications:
- Invest in **primary and secondary education**
- Strengthen **family planning** programs
- Improve **infrastructure and communication access**

---

## Future Work

- Integrate **post-2014 data** to update global literacy trends
- Develop a **time-series analysis** to study policy effects over time
- Deploy the final **Gradient Boosting model** as a web application to allow users to explore custom scenarios
