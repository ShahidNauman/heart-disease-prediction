# Heart Disease Prediction

## Objective:

Build a model to predict whether a person is at risk of heart disease based on their health data.

## Dataset:

Heart Disease UCI Dataset (available on Kaggle)

## Instructions:

- [x] Clean the dataset (handle missing values if any).
- [x] Perform Exploratory Data Analysis (EDA) to understand trends.
- [x] Train a classification model (Logistic Regression or Decision Tree).
- [x] Evaluate using metrics: accuracy, ROC curve, and confusion matrix.
- [x] Highlight important features affecting prediction.

## Skills:

- Binary classification
- Medical data understanding and interpretation
- Model evaluation using ROC-AUC and confusion matrix
- Feature importance analysis

## 🌳 Decision Tree – Most Important Features

### Top Predictors (Tree)

| Feature                      | Importance | Interpretation                           |
| ---------------------------- | ---------- | ---------------------------------------- |
| **exang_True**               | 0.362      | Strongest predictor                      |
| **chol**                     | 0.225      | High cholesterol strongly impacts splits |
| **age**                      | 0.103      | Older patients higher risk               |
| **sex_Male**                 | 0.067      | Males higher risk                        |
| **cp_atypical angina**       | 0.062      | Chest pain type important                |
| **thalch**                   | 0.058      | Max heart rate informative               |
| **trestbps**                 | 0.045      | Resting BP moderate influence            |
| **ca**                       | 0.026      | Number of vessels                        |
| **thal_normal**              | 0.023      | Thalassemia status                       |
| **restecg_st-t abnormality** | 0.012      | ECG abnormality                          |

### 🧠 Interpretation (Tree)

The model’s decision-making hierarchy:

1. **Exercise-induced angina (exang)** is the dominant split driver.
2. Cholesterol and age follow as strong structural split features.
3. Sex and chest pain type are secondary discriminators.

The tree focuses on features that best partition the dataset early.

## 📈 Logistic Regression – Coefficient Interpretation

Unlike the tree, logistic regression shows **direction of influence**.

### Top Coefficients (absolute importance order)

| Feature                | Coefficient | Meaning                                                               |
| ---------------------- | ----------- | --------------------------------------------------------------------- |
| **cp_atypical angina** | -0.765      | Strongly decreases disease probability                                |
| **ca**                 | +0.542      | More vessels → higher risk                                            |
| **oldpeak**            | +0.501      | ST depression increases risk                                          |
| **exang_True**         | +0.496      | Exercise angina increases risk                                        |
| **cp_non-anginal**     | -0.491      | Non-anginal pain lowers risk                                          |
| **sex_Male**           | +0.489      | Males higher risk                                                     |
| **chol**               | -0.448      | Higher cholesterol associated with lower predicted risk (interesting) |
| **slope_flat**         | +0.371      | Flat ST slope increases risk                                          |
| **age**                | +0.292      | Older age increases risk                                              |
| **thalch**             | -0.255      | Higher max HR reduces risk                                            |

## 🔎 Key Observations

### 🔴 Strong Risk Indicators (Positive Coefficients)

- exang_True
- ca
- oldpeak
- sex_Male
- slope_flat
- age

These align strongly with cardiology knowledge.

### 🟢 Protective Indicators (Negative Coefficients)

- cp_atypical angina
- cp_non-anginal
- thalach (max heart rate)
- chol (unexpectedly negative)

### About Cholesterol

The negative coefficient suggests:

- In your dataset, cholesterol may correlate with other variables.
- Multicollinearity might be influencing its sign.
- Or scaling effects are interacting.

This is common in logistic regression.

## 🔄 Tree vs Logistic – Important Comparison

| Aspect                 | Decision Tree | Logistic Regression |
| ---------------------- | ------------- | ------------------- |
| Top Feature            | exang         | cp_atypical angina  |
| Direction shown?       | ❌ No         | ✅ Yes              |
| Captures interactions? | ✅ Yes        | ❌ Linear           |
| Interpretability       | Rule-based    | Probability-based   |

## 🏥 Clinically Meaningful Overlap

Both models agree that:

- Exercise-induced angina is critical
- Age matters
- Sex matters
- Chest pain type is important
- Number of vessels (ca) is important

When two different model types agree →
That strongly suggests these are real signals.

## 📌 Final Professional Interpretation (For Report)

You can write:

> Feature importance analysis revealed that exercise-induced angina, chest pain type, ST depression, number of major vessels, age, and sex were the most influential predictors of heart disease. Both the Decision Tree and Logistic Regression models consistently identified these variables, reinforcing their clinical relevance. The alignment between models suggests robust predictive signals rather than model-specific artifacts.

## 🎯 Most Important Feature Overall?

**Exercise-induced angina (exang)**

It dominates the tree and has a strong positive coefficient in logistic regression.

That’s your strongest predictor.
