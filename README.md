# 🎓 Student Grade Repetition Prediction

This project was completed as part of the **Dataiku ML Practitioner Certificate**. The goal is to help educational institutions identify students at risk of repeating an academic year and generate actionable insights for early intervention.

---

## 📌 Project Overview

- **Objective:** Predict whether a student will repeat an academic year based on demographic, social, and academic features.
- **Dataset:** Student performance dataset adapted from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Student+Performance).
- **Tool Used:** Dataiku 13.3

---

## 🧠 Problem Statement

An education-focused organization is working to improve student outcomes. We are tasked with building a machine learning model that predicts if a student will repeat a grade, using data across four schools (GP, LT, MS, RC), and derive insights that could influence student success initiatives.

---

## 📁 Dataset Description

The `schools_data` dataset includes:
- **Student characteristics:** study time, free time, number of absences, grade.
- **Socioeconomic indicators:** travel time, parental marital status, internet access.
- **Target Variable:** `repeated` — binary variable indicating if the student repeated the year.

---

## 🛠️ Project Workflow

### 1. 🧪 Exploratory Data Analysis (EDA)
- Ensured `grade` was numeric and `repeated` was categorical.
- Analyzed:
  - `grade` distribution
  - `grade` by `school`
  - `grade` by `failures`
  - `repeated` by travel time and absences
- Found high repetition rates among students with:
  - **Travel time ≥ 2 hours**
  - **Absences ≥ 8**

### 2. 🧹 Data Preparation
- Split data into:
  - `train_data`
  - `validation_data`
- Used the `data_perimeter` column for splitting.

### 3. 🤖 Baseline Modeling
- Algorithms used: **Random Forest**, **Logistic Regression**
- Target: `repeated`
- Removed `grade` feature to avoid **data leakage**.

### 4. ⚙️ Diagnostics & Assertions
- Added **ML Assertion** to ensure model expectations align:
  - For students with travel time ≥ 2 and absences ≥ 8:
    - Expected class: 1 (`repeated`)
    - Valid ratio: 22%

### 5. 📈 Model Evaluation
- Evaluated models using:
  - **AUC Score**
  - **Confusion Matrix**
  - **Partial Dependence Plots**
- Best performing model based on AUC: **[Insert Best Model Name]**

### 6. 🚀 Model Deployment
- Deployed best model to Flow.
- Scored `validation_data` using the **Score recipe**:
  - Created `validation_scored` with selected input columns: `school`, `repeated`.
  - Enabled **individual prediction explanations**.

### 7. 🧾 Final Analysis
- Added `prediction_correct` column to evaluate model accuracy.
- Analyzed correct prediction percentage by school:
  - GP: XX%
  - LT: XX%
  - MS: XX%
  - RC: XX%

---

## 🔍 Key Learnings

- High absenteeism and long commute times are strong indicators of academic risk.
- ML assertions help ensure the model meets **business logic and expectations**.
- Data leakage can significantly inflate model performance — always remove derived features like `grade` if target is related.

---

## 💡 Tools & Technologies

- **Platform:** Dataiku (Visual ML, Flow, Score recipe)
- **Algorithms:** Logistic Regression, Random Forest
- **Concepts:** Data splitting, assertions, model explainability, AUC, PDPs

---

## 📄 License

This project was created for certification purposes. Do not reuse without permission from Dataiku and the author.

---

## 📬 Contact

For questions or collaboration:  
[Your Name]  
[LinkedIn Profile] | [GitHub Profile] | [Email]
