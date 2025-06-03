
# Student Academic Year Repetition Prediction

## Project Overview

This project aims to predict whether a student is at risk of repeating an academic year and to generate actionable insights to improve student outcomes. Leveraging the Student Performance Dataset from the UCI Machine Learning Repository, we develop and evaluate machine learning models, specifically Random Forest and Logistic Regression, to identify at-risk students.

## Problem Statement

An organization is seeking to identify students who are likely to repeat an academic year. The goal is to build a predictive model that can accurately flag these students, allowing for targeted interventions to support their success.

## Dataset

The project utilizes a modified version of the [Student Performance Dataset](https://archive.ics.uci.edu/ml/datasets/Student+Performance) from the UCI Machine Learning Repository.

The primary dataset used is `schools_data`, a CSV file containing information for four schools (GP, LT, MS, RC). This data includes:

* **Student characteristics:** Such as study time, free time, and number of absences.
* **Geographical and socioeconomic indicators:** Such as travel time, home internet access, and parental marital status.

## Project Structure & Methodology

This project follows a typical machine learning workflow, implemented within the Dataiku platform.

### 1. Project Setup (Dataiku)

* **Installation:** The project was initiated in Dataiku 13.3+ by installing the "ML Practitioner Assessment" learning project.
* **Access:** The project Flow was accessed to begin data manipulation and model building.

### 2. Exploratory Data Analysis (EDA) - Statistics Worksheets

Initial data exploration and analysis were performed using Dataiku's Statistics Worksheets to understand the distributions and relationships within the `schools_data` dataset.

* **`grade`:** Examined its numerical distribution.
* **`grade` by `school`:** Analyzed grade distributions across different schools.
* **`grade` by `failure`:** Investigated the relationship between grades and past failures.
* **`repeated`:** Ensured this column was treated as a categorical variable for binary classification.
* **Key Factor Analysis:** Created a chart to analyze the proportion of students who repeat a grade based on the following combined factors:
    * Travel time $\ge$ 2 hours
    * Number of absences $\ge$ 8

### 3. Data Preparation

* **Data Splitting:** The `schools_data` dataset was split into `train_data` and `validation_data` based on the values in the `data_perimeter` column. This ensures a clean separation for model training and independent evaluation.

### 4. Baseline Model Creation (Visual Analysis Lab)

A baseline machine learning model was trained using the `train_data` dataset within Dataiku's Lab for Visual Analysis.

* **Target Variable:** The `repeated` column was set as the target, indicating whether a student repeated an academic year.
* **Algorithms:**
    * **Random Forest:** Utilized with default settings.
    * **Logistic Regression:** Utilized with default settings.

### 5. Model Results Inspection

The results of the baseline models were thoroughly examined in the "Result" tab of the Dataiku Lab.

* **Diagnostics:** Investigated diagnostics findings (by hovering over "Diagnostics") to identify initial issues or warnings flagged by Dataiku regarding the model.

### 6. Model Design Iteration & Improvement

To improve model performance and address identified diagnostics, the model design was refined:

* **Feature Removal:** The `grade` column was explicitly removed as a model feature from the "Design settings" of the machine learning task. This was a critical step to **prevent data leakage**, as the `repeated` column (our target) is computed based on `grade`. Including `grade` as a feature would give the model direct access to information that it's trying to predict, leading to artificially inflated performance.
* **ML Assertion:** An ML assertion was created in the "Debugging" tab to ensure the model aligns with business expectations for specific known cases:
    * **Condition:** Students with travel time $\ge$ 2 hours AND number of absences $\ge$ 8.
    * **Expected Class:** 1 (repeated).
    * **Valid Ratio:** 22%. This assertion helped validate the model's behavior on a high-risk subgroup.

* **Retraining:** The Random Forest and Logistic Regression algorithms were retrained with the updated design.

### 7. Model Performance Interpretation (Session 2)

The performance of the retrained models (Session 2) was analyzed in detail:

* **Best AUC:** Determined which algorithm achieved the best Area Under the Curve (AUC), a key metric for classification models.
* **Most Important Features:** Identified the top influential features for both Random Forest and Logistic Regression models. This provides insights into which factors are most predictive of repetition.
* **Confusion Matrix:** Examined the confusion matrix for each model to understand true positives, true negatives, false positives, and false negatives.
* **Partial Dependence Plots:** Analyzed the partial dependence for the `studytime` feature in the Logistic Regression model to understand its marginal effect on the prediction.
* **ML Assertion Result:** Verified whether the previously set ML assertion passed or failed, indicating if the model met the expected behavior for the specified high-risk group.

### 8. Model Deployment & Evaluation

The best-performing model (based on AUC) was deployed to the Dataiku Flow.

* **Score Recipe:** A Score recipe was used to evaluate the deployed model on the unseen `validation_data` dataset.
    * **Output Dataset Name:** `validation_scored`.
    * **Output Columns:** Only `school` and `repeated` were kept as input columns in the output dataset for convenience.
    * **Individual Explanations:** Individual prediction explanations were computed to understand why the model made a specific prediction for each student.

### 9. Final Analysis

The `validation_scored` dataset was further prepared and analyzed:

* **`prediction_correct` Column:** A new column, `prediction_correct`, was created to indicate whether the model's prediction matched the actual `repeated` status.
* **Distribution Analysis:** The distribution of `prediction_correct` by school was analyzed.
* **Percentage Correct by School:** The percentage of correct predictions for each school was calculated, providing a school-specific view of model accuracy.

## Key Findings & Insights

* *(This section should be filled in after you complete the project and have concrete findings from your analysis.)*
    * Which model performed best (Random Forest or Logistic Regression)?
    * What were the most significant features influencing student repetition?
    * Did the ML assertion pass, and what does that imply about the model's reliability for the specific high-risk group?
    * How did the model perform across different schools? Are there schools where the model is more or less accurate?
    * Any surprising or actionable insights from partial dependence plots or feature importance?

## Technologies Used

* **Dataiku:** For end-to-end machine learning project lifecycle management (data preparation, model training, evaluation, deployment).
* **Python (within Dataiku):** Underlying language for various recipes and coding within Dataiku.
* **Machine Learning Algorithms:** Random Forest, Logistic Regression.

## How to Replicate

1.  **Install Dataiku:** Ensure you have Dataiku 13.3+ installed.
2.  **Create New Project:** From the Dataiku Design homepage, select `+ New Project`.
3.  **Learning Projects:** Choose `Learning projects` and search for `ML Practitioner Assessment`.
4.  **Install:** Install the project into your desired folder.
5.  **Go to Flow:** Navigate to the project's Flow (`g + f`).
6.  **Follow Instructions:** Follow the instructions outlined in the "Project Structure & Methodology" section to replicate the data preparation, model training, and analysis steps.

---
