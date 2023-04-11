# Breast Cancer Wisconsin: Data Analysis & Interpretation

## Introduction

For my final project, I sought to analyze a dataset related to medicine, a common area of interest within our group. The dataset I selected was the Breast Cancer Wisconsin Diagnostic Data Set (link: https://bit.ly/3Kyp8ta). Available since 1995, this dataset was constructed by 3 researchers from the University of Wisconsin, and has been cited in more than 30 papers since its original release. The dataset features observations collected from "a digitized image of a fine needle aspirate (FNA) of a breast mass," and describes "the cell nuclei present in the image." The dataset was created in order to study the visual characteristics of malignant and benign tumors. I believe that this dataset will provide me with a great opportunity to develop and hone my prediction and classification skills. My ultimate goals were to 1) determine which features are most indicative of cancerous growth and 2) construct a tool that can predict whether a mass is cancerous based on input data.

This project includes:

- notebook.ipynb: core notebook
- data.csv: dataset
- dictionary.xlsx: A data dictionary explaining the dataset features

## Key Audiences

- Medical Professionals & Institutions
- Medical Technology Firms

## Requirements

- matplotlib 3.5.1
- numpy 1.22.0
- pandas 1.3.5
- seaborn 0.11.2
- sklearn 1.0.2
- IPython 7.30.1
- jupyter_client 7.1.0
- jupyter_core 4.9.1
- jupyterlab 3.2.5
- notebook 6.4.6

## Key Custom Functions

- run_classifier: This function returns a classification and confusion matrix for a given classification model. This function accepts a classifier type + training and testing data as parameters
- correlated: This function returns attributes that are correlated more than a given a threshold.
- feature_importance: This function will run a classification model with one feature type at a time. It will then compare the performance of the single feature type model to the performance of the full model. The function will output a grid displaying the performance comparison for key metrics.

## Approach

1. Data Intake
2. Standardization
3. Visualization + EDA
4. Hypothesis Formulation
5. Classification Pre-Processing
   - Create Dataset w/ Correlated Features Removed
   - Train/Test Split
   - Principal Component Analysis (PCA)
6. Classification Modeling
   - Logistic Regression
   - Random Forest
   - Gradient Boosting
   - KNeighbors
7. Measure & Compare Outcomes
   - How does performance compare when using all features vs. only uncorrelated?
   - Determine Feature Importance
   - Compare Precision, Recall, F1
   - Perform Cross-Validation
   - Compare PCA Results vs. Non-PCA Results

## Analysis of Results

Based on initial exploratory data analysis, I anticipated that 1) the dataset would respond well to classification modeling and that 2) the concave_points feature group would be an important indicator. Ultimately, my intuitions were at least partially validated, but I was surprised by some of the results as well.

Given the nature of the data, the classification performance statistic that I most concerned with was recall. As a life-threatening disease, I did not want to overlook any possible cancer diagnoses. Although all the classification models I used produced good results, I believe that logistic regression (with correlated features removed) produced the best overall results with a 98% recall score and a 98% precision score. The cross-validation results were also promising, producing ~98% accuracy with a standard deviation of ~1%, mitigating immediate concerns about over-fitting.

I also re-ran our classification models on a dataset where we applied principal component analysis (PCA). Since PCA is a popular technique, the goal was to see how the classification results changed (if at all) with PCA applied. After discussions with my professor, I understood that PCA's effect on modeling performance may not be noticeable in all cases, and can depend on the nature of the data, as well as the hyperparameter setting. Dimensionality reduction is often required when the dataset's columns outnumber the dataset's rows. In this case, I did not notice a large difference when running the classification models on PCA and non-PCA data, and I believe this is due to the size and structure of our dataset. However, I did notice a significant dip in the predictive performance of the PCA classifiers when I first removed correlated features, and then subsequently applied PCA to the data. For this reason, I chose not to remove correlated features from our PCA dataset. I look forward to continuing to explore PCA in other contexts.

The final goal was to determine which features were most important to the classification modeling. After testing various techniques, I settled on an approach where I ran each feature group (i.e. radius, concave_points) through the model by itself, and then compared the performance scores to how the model performed with all feature groups included. With this technique applied, the radius feature group lead the way, surrendering only ~7% in terms of recall. Overall, it seemed that concavity and measures of size (i.e. radius) were the most important indicators of malignancy. On the other hand, feature groups like symmetry and smoothness seemed to contribute significantly less to the model's classification performance.

## Future Enhancements

- Add a patient "age" feature to the dataset
- Expand the number of observations
- Build towards an "unsupervised" learning model
- Utilize a data collection technique that is less invasive than FNA

## Conclusion

I believe that this particular project offered me a great opportunity to develop my data analysis and interpretation skills in a significant way. I was forced to explore new tools and techniques, while evaluating data with real-world importance. I believe this project has given me the skills and confidence to work on similar projects in the future.
