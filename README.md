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
  - **Travel t**
