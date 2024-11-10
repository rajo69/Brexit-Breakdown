# Brexit Breakdown: A Statistical Exploration of Demographic Influences on Brexit Voting Patterns

**Author:** Rajarshi Nandi  
**Date:** 2024-05-10  

This repository contains the R code and analysis for the statistical exploration of demographic influences on Brexit voting patterns. The project leverages clustering and logistic regression techniques to analyze socio-demographic data from electoral wards and their Brexit referendum responses.

---

## Online Report

View the report online on RPubs

[Brexit Breakdown](https://rpubs.com/rajo2024/1243720)

## Table of Contents

1. [Introduction](#introduction)  
2. [Dataset Overview](#dataset-overview)  
3. [Key Analyses](#key-analyses)  
    - [K-Means Clustering](#k-means-clustering)  
    - [Logistic Regression](#logistic-regression)  
    - [Model Interpretability](#model-interpretability)  
    - [Alternative Logistic Regression](#alternative-logistic-regression)  
4. [Findings](#findings)  
5. [Requirements](#requirements)  
6. [Usage](#usage)  
7. [Conclusion](#conclusion)  

---

## Introduction

The Brexit referendum in 2016 was a landmark event in UK politics. This project investigates the influence of socio-demographic factors such as income, age, education level, and ethnicity on Brexit voting patterns. Using clustering and regression techniques, the analysis aims to uncover trends and correlations within the data.

---

## Dataset Overview

The dataset used in this project includes socio-demographic statistics for electoral wards. It contains the following variables:

- `abc1`: Proportion of individuals in upper or middle-class social grade.
- `notBornUK`: Proportion of residents not born in the UK.
- `medianIncome`: Median income level of the ward.
- `medianAge`: Median age of residents.
- `withHigherEd`: Proportion of residents with university-level education.
- `voteBrexit`: Binary response indicating whether the ward voted to leave the EU.

**Dataset Sample:**
| abc1      | notBornUK | medianIncome | medianAge | withHigherEd | voteBrexit |
|-----------|-----------|--------------|-----------|--------------|------------|
| 0.1336406 | 0.0126050 | 0.2525773    | 0.5000000 | 0.08552632   | TRUE       |
| 0.1290323 | 0.1134454 | 0.1082474    | 0.2727273 | 0.1118421    | TRUE       |

---

## Key Analyses

### 1. K-Means Clustering

- **Objective:** To cluster wards based on demographic factors and analyze their association with Brexit voting patterns.
- **Findings:**
  - Optimal clusters determined using the `NbClust` library suggested 2 clusters.
  - Cluster boundaries fit some variable combinations but were not predictive of the `voteBrexit` outcome.

**Visualization:** 
- Cluster plots showed minimal overlap between clusters and Brexit voting patterns.

---

### 2. Logistic Regression

- **Objective:** To determine the significance of demographic variables in predicting Brexit voting patterns.
- **Key Results:**
  - Variables `abc1`, `notBornUK`, `medianIncome`, `medianAge`, and `withHigherEd` were significant.
  - Strongest effects:
    1. `withHigherEd` (negative)
    2. `abc1` (positive)

---

### 3. Model Interpretability

Factors affecting model interpretability:
- **Collinearity:** High correlation among `abc1`, `medianIncome`, and `withHigherEd` reduced clarity.
- **Interaction Patterns:** Variables like `notBornUK` and `medianAge` showed independence and higher reliability.

**Approach:** 
- Correlation analysis identified collinear variables.
- Hierarchical clustering was used to visualize relationships.

---

### 4. Alternative Logistic Regression

- **Refinement:** Model re-trained using independent variables (`notBornUK`, `medianAge`, `withHigherEd`).
- **Key Results:** 
  - `withHigherEd` remained the most significant factor.
  - Reduced standard errors improved clarity but increased the AIC score, indicating potential underfitting.

---

## Findings

- **Higher Education (`withHigherEd`)**: Wards with a higher proportion of university-educated residents were more likely to vote to remain.
- **Social Class (`abc1`)**: Higher proportions of middle/upper-class residents correlated positively with voting to leave.
- **Median Age & Non-UK Born Population:** Played secondary but relevant roles.

Comparison with *The Guardian* analysis showed alignment, emphasizing education as the strongest predictor.

---

## Requirements

- **R Version:** 4.0 or later  
- Required Libraries:
  - `ggplot2`
  - `NbClust`
  - `corrplot`
  - `boot`

Install dependencies using:
```R
install.packages(c("ggplot2", "NbClust", "corrplot", "boot"))
```

---

## Usage

1. Clone this repository:
   ```bash
   git clone https://github.com/your-repo-url.git
   ```
2. Open the R script and set the working directory to the location of the dataset.
3. Run the script to generate the analyses and visualizations.

---

## Conclusion

This project demonstrates the application of statistical methods to analyze complex socio-political events. While education emerged as the most significant factor, collinearity among variables underscores the importance of careful feature selection.

---

## Future Work

- Explore ensemble methods (e.g., random forests) for improved predictions.
- Extend the dataset with additional demographic or geographic features for deeper insights.
