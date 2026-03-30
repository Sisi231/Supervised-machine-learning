![R](https://img.shields.io/badge/language-R-blue)
![RMarkdown](https://img.shields.io/badge/tool-RMarkdown-lightgrey)
![Status](https://img.shields.io/badge/status-Completed-brightgreen)

# Supervised Learning for Diabetes Prediction (NHANES)
This project applies multiple supervised learning techniques to predict whether an individual has diabetes using health and socioeconomic data from the NHANES dataset.
The goal is not only to build accurate models, but to prioritize **high specificity**, minimizing false negatives given their severe real-world health impact.


# Dataset
- **Source:** NHANES (National Health and Nutrition Examination Survey)
- **Observations:** ~10,000  
- **Variables:** 76  
- **Target Variable:** Diabetes (binary classification)

The dataset includes demographic, health, and lifestyle variables such as age, weight, cholesterol levels, and blood pressure.

# Methods

# Data Processing
- Handling missing values using:
  - Mode (categorical)
  - Mean (numerical by age groups)
- Feature engineering:
  - SleepAdjusted variable
  - BMI categorization
- Outlier removal and normalization

# Models Implemented
- **Linear Discriminant Analysis (LDA)**
- **Quadratic Discriminant Analysis (QDA)**
- **Logistic Regression**
- **Penalized Logistic Regression (Lasso/Ridge via glmnet)**
- **Decision Tree**
- **Random Forest**
- **Gradient Boosting Model (GBM)**

# Model Evaluation Focus
Due to class imbalance, evaluation prioritizes:
- **Specificity** (correctly identifying diabetic patients)
- **Balanced Accuracy**

# Key Results
- **Best Model:** Penalized Logistic Regression  
  - Specificity: **~88%**  
  - Balanced Accuracy: **~79%**

- **Decision Tree:**  
  - Strong interpretability  
  - Specificity: ~82%

- **GBM:**  
  - Balanced performance (~0.74 specificity, ~0.76 balanced accuracy)

- **Random Forest:**  
  - Lower performance in detecting diabetic cases

# Key Insights
- Most important predictors:
  - Age
  - Cholesterol (TotChol)
  - Weight
  - Blood Pressure (BPSysAve)
  - Marital Status

- Higher risk of diabetes is associated with:
  - Older age
  - Higher weight
  - Higher blood pressure

- Dataset imbalance significantly impacts model behavior → requires careful metric selection

# Model Interpretation

- **Partial Dependence Plots (PDP)** used to analyze feature effects  
- **SHAP values** used for:
  - Feature importance
  - Individual prediction explanations

These methods provide transparency into how models make predictions.

# Health Impact Analysis
A custom scoring system was designed:
- True Positive: +10  
- False Positive: -1  
- False Negative: -15  

The final model yields a **positive overall health impact**, meaning correct diagnoses outweigh harmful misclassifications.

# Tech Stack
**Language:**  
- R  

**Libraries:**  
- dplyr, tidyverse, ggplot2, GGally  
- MASS, glmnet, e1071  
- rpart, randomForest, gbm  
- caret, pROC  
- mice, VIM, skimr  
- pdp, fastshap, reshape2  

# How to Run

1. Open the `.Rmd` file and run all chunks

2. Load dataset:
install.packages("NHANES")
library(NHANES)

If it fails, run:
NHANES <- read.csv("NHANES_data.csv")

3. Alternatively:

Open the .html file to view results directly

# Project Structure
README.md
report/
│   └── Report.pdf
notebook/
│   ├── Statistical_Learning_Project.Rmd
│   └── Statistical_Learning_Project.html
