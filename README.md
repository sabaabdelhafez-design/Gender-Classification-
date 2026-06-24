# Gender-Classification-
Applied Probability and Math concepts in Data Science 
Project Structure

1. Data Ingestion & Preprocessing


Load health data from Excel file
Column renaming for abbreviated notation (Gender → G, Weight_kg → W, Height_cm → H, Cholesterol_mg_dL → C, Diabetes → D)
Data Quality Checks:

Missing values inspection
Duplicate record detection
Summary statistics review



Outlier Handling: IQR-based clipping for numeric columns
Encoding: Label encoding for categorical Gender variable (0 = Female, 1 = Male)


2. Probability Distribution Analysis

Probability Mass Function (PMF)


Histogram-based empirical probability calculation using relative frequency normalization
Visualization of PMFs before and after normalization
Bin-width comparison (5, 10, 20 bins) to analyze sensitivity to binning choices


Key Finding: All three variables show reasonable empirical distributions without extreme skewness.

Cumulative Distribution Function (CDF)


Empirical CDF calculation from sorted data
Visual representation of cumulative probability vs. variable values
Shows the proportion of data below each point


3. Descriptive Statistics

For each variable (C, W, H), computed:


Mean: Central tendency measure
Variance: Spread around the mean
Skewness: Asymmetry of distribution
Kurtosis: Tail heaviness of distribution


All Variables Summary:


Cholesterol (C): Mean ≈ moderate, slight asymmetry
Weight (W): Positive correlation with variance
Height (H): Well-centered with low variance


4. Gaussian Distribution Fitting


Overlay normal distribution curves on histograms
Compare empirical data distribution with theoretical Gaussian fit
Assess goodness-of-fit visually using density plots


Insight: Most variables approximate normal distributions reasonably well, validating parametric statistical approaches.

5. Correlation & Covariance Analysis

Overall Dataset:

PairCovarianceCorrelation(C, W)-0.162(C, H)--0.043(W, H)--0.054

Key Findings:


All correlations are very weak (< 0.2 in absolute value)
Variables are largely independent in linear terms
(C, W) shows weakest positive correlation
(C, H) and (W, H) show negligible negative correlations


Correlation Heatmap:

Visual representation of correlation matrix with color-coded strength values.

6. Gender-Stratified Analysis

Complete re-analysis for Female (G=0) and Male (G=1) subgroups:


Separate PMF and CDF visualizations
Independent descriptive statistics calculation
Gender-specific correlation matrices
Bin-width sensitivity analysis


Enables: Identification of potential gender-based differences in health metrics distributions and relationships.

7. Linear Regression Modeling

Model 1: Weight from Height (WfH)

WfH = β₀ + β₁ × H


Purpose: Predict weight based on height
Metrics:

Correlation coefficient (W vs WfH)
R² Score
Mean Absolute Error (MAE)
Root Mean Squared Error (RMSE)



Visualization: Scatter plot with regression line overlay


Model 2: Diabetes from Cholesterol (DfC)

DfC = β₀ + β₁ × C


Purpose: Linear model for binary classification (Diabetes prediction)
Limitations: Linear regression on binary outcome; classification models better suited
Output: Predicted probability values, actual vs. predicted scatter plots


8. Machine Learning Classification

Gaussian Naive Bayes Classifier


Objective: Predict Diabetes status (D) from multiple features
Features: Gender (G), Weight (W), Height (H), Cholesterol (C)
Data Split: 80% training, 20% testing (random_state=42)
Model Type: Probabilistic classifier based on Bayes' theorem with Gaussian feature assumption


Evaluation Metrics:


Accuracy Score: Proportion of correct predictions
Confusion Matrix: True/False Positives and Negatives
Classification Report: Precision, Recall, F1-Score per class



Key Findings & Insights


Weak Inter-Variable Relationships: Health metrics show independence, suggesting multifactorial disease etiology
Near-Normal Distributions: Variables approximate Gaussian distributions, validating parametric tests
Gender Stratification: Analysis enables comparison of distributions between genders
Predictive Power: Linear models have limited predictive power (low R²); machine learning provides better classification
Diabetes Prediction: Naive Bayes model captures non-linear relationships better than linear regression



Technologies & Libraries


Python 3.x
pandas: Data manipulation and analysis
NumPy: Numerical computations
scikit-learn: Machine learning models (LinearRegression, GaussianNB, train_test_split, metrics)
SciPy: Statistical distributions and functions
Matplotlib: Data visualization
Seaborn: Statistical data visualization
openpyxl/pandas: Excel file I/O



File Requirements


Data.xlsx - Input health dataset with columns: Gender, Weight_kg, Height_cm, Cholesterol_mg_dL, Diabetes



Usage


Ensure all required libraries are installed:


bash   pip install pandas numpy scikit-learn scipy matplotlib seaborn openpyxl


Place Data.xlsx in the working directory
Run the notebook:


bash   jupyter notebook probability_project_final_version.ipynb


Execute cells sequentially to generate:

Cleaned dataset with encoded variables
PMF and CDF visualizations
Descriptive statistics tables
Gaussian overlay plots
Correlation heatmaps
Gender-specific analyses
Regression model results
Classification model evaluation






Workflow Summary

Data Loading
    ↓
Data Cleaning & Outlier Handling
    ↓
Label Encoding (Gender)
    ↓
Exploratory Probability Analysis
├─ PMF Computation & Visualization
├─ CDF Analysis
└─ Bin-width Sensitivity
    ↓
Descriptive Statistics & Distribution Fitting
├─ Mean, Variance, Skewness, Kurtosis
└─ Gaussian Overlay Validation
    ↓
Correlation & Covariance Analysis
├─ Pairwise correlations
└─ Heatmap visualization
    ↓
Gender-Stratified Analysis
└─ Repeat all above for F & M subgroups
    ↓
Predictive Modeling
├─ Linear Regression (W from H, D from C)
└─ Gaussian Naive Bayes Classification (D from all features)
    ↓
Model Evaluation & Interpretation


Notes
Outlier Treatment: IQR clipping preserves extreme values within physically realistic bounds
Correlation Interpretation: Weak correlations suggest independent variables; multicollinearity not a concern
Classification Choice: Gaussian Naive Bayes chosen for its probabilistic foundation aligned with course emphasis
Binary Outcome Challenge: Linear regression on binary targets (Diabetes) produces probability estimates; classification metrics more appropriate
impact on my skils
This project demonstrates applied probability, statistics, and machine learning concepts including:
Empirical probability distributions (PMF/CDF)
Parametric statistics (mean, variance, distribution fitting)
Correlation analysis
Linear regression
Probabilistic classification (Naive Bayes
