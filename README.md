# Time Series Classification: Binary and Multiclass Classification

This repository extends the feature extraction process from the **AReM dataset** and delves into binary and multiclass classification tasks. The primary focus is on logistic regression and its variants, with comparisons to other methods like Naïve Bayes for multiclass classification.

---

## Table of Contents

- [Introduction](#introduction)
- [Data](#data)
- [Project Tasks](#project-tasks)
  - [Binary Classification Using Logistic Regression](#binary-classification-using-logistic-regression)
  - [Binary Classification Using L1-Penalized Logistic Regression](#binary-classification-using-l1-penalized-logistic-regression)
  - [Multi-class Classification](#multi-class-classification)
- [Results](#results)
---

## Introduction

This project builds upon time-domain features extracted from the **Activity Recognition System based on Multisensor Data Fusion (AReM)** dataset to address:
1. Binary classification of bending versus other activities.
2. Multi-class classification for all seven activities using logistic regression and Naïve Bayes classifiers.

---

## Data


### Dataset Details:
- **Activities**: Bending1, Bending2, Cycling, Lying, Sitting, Standing, Walking.
- **Files**: Each file contains six time series with 480 values each:
  - avg rss12, var rss12, avg rss13, var rss13, avg rss23, var rss23.
- **Statistics**:
  - Total instances: 88.

---

## Project Tasks

### Binary Classification Using Logistic Regression
1. **Visualization**:
   - Scatterplots of selected features (e.g., Min, Mean, Max) from time series 1, 2, and 6 to distinguish *bending* vs. *other activities*.

2. **Feature Expansion**:
   - Split each time series into two halves, creating 12 time series per instance.
   - Repeat scatterplots for the expanded features and compare with the original.

3. **Segmentation and Feature Selection**:
   - Segment time series into equal-length segments.
   - Perform logistic regression to solve the binary classification problem.
   - Use:
     - **p-values** from logistic regression coefficients.
     - **Recursive Feature Elimination (RFE)** or backward selection to prune features.
   - Perform 5-fold cross-validation to determine the best combination of \( l \) and \( p \) (number of features).

4. **Handling Class Imbalance**:
   - Use **stratified cross-validation** to address class imbalance during training.

5. **Performance Evaluation**:
   - Report:
     - Confusion matrix.
     - ROC curve and AUC.
     - Logistic regression coefficients (\( \beta_i \)) and associated p-values.

---

### Binary Classification Using L1-Penalized Logistic Regression
1. **Regularization**:
   - Repeat segmentation experiments from the previous section using **L1-penalized logistic regression**.
   - Perform cross-validation for:
     -  Number of time series segments.
     -  Regularization penalty weight.

2. **Comparison**:
   - Compare L1-penalized logistic regression with feature selection using p-values.
   - Evaluate based on model performance, interpretability, and ease of implementation.

---

### Multi-class Classification
1. **L1-Penalized Multinomial Regression**:
   - Determine the optimal \( l \) from previous experiments.
   - Train an L1-penalized multinomial regression model for all activities.
   - Evaluate performance using confusion matrices, test errors, and ROC curves.

2. **Naïve Bayes Classifier**:
   - Train classifiers using both Gaussian and Multinomial priors.
   - Compare their performance with multinomial regression.

3. **Comparison**:
   - Assess which method performs better for multi-class classification in terms of accuracy, interpretability, and computational efficiency.

---

## Results

- **Binary Classification**:
  - Logistic regression and L1-penalized regression demonstrated high accuracy.
  - Feature expansion and segmentation improved classification performance.
- **Multi-class Classification**:
  - Multinomial regression outperformed Naïve Bayes in most scenarios.
  - Gaussian Naïve Bayes performed better for certain feature subsets.

---
