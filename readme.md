<h1 align=center> Task 1 : The CampusPulse Initiative <img src='https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcjdrOGhwYjNmd3YzMW0ybnJqaWxwcGw5cmk4YW82OXI3amJlaGRjYyZlcD12MV9zdGlja2Vyc19zZWFyY2gmY3Q9cw/GrPgFtvyLlgElFiO7m/giphy.gif' width = 40 height = 30></h1>

Dataset: [Student Data](Dataset.csv)<br>
Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `sklearn`, `shap` <br>
Notebook: [Task 1](Task_1.ipynb)
## Objectives 🎯
- To recover three anonymized features from the Dataset using EDA techniques
- Cleaning and preprocessing the data
- Performing **exploratory data analysis (EDA)**, uncover insights from the data and plot visualizations to better understand the relationships between features
- Building multiple machine learning models(*classifiers*) to predict the target variable `romantic` and comparing their performance.
- Using `SHAP` to interpret the model and understand the impact of features on the predictions
- Generate local explanations for two students one predicted `yes` and one predicted `no`
- Interpret the results and find what drives the model's predictions
- Bonus: Identify the algorithm that produced the **decision boundary** plot from visual clues like linearity, complexity and shape of the decision boundary and explain your reasoning

## Project Workflow ⚙️
The notebook is organized into the following sections:
- <u>[Level 0](#level-0-importing-libraries-and-dataset-summary)
- [Level 1](#level-1-variable-identification-protocol)
- [Level 2](#level-2-data-integrity-audit)
- [Level 3](#level-3-exploratory-insight-report)
- [Level 4](#level-4-relationship-prediction-model)
- [Level 5](#level-5-model-reasoning-and-interpretation)
- [Bonus Level](#bonus-level-boundary-match)</u>

## Level 0: Importing Libraries and Dataset Summary
- Load the dataset and import the necessary libraries
- Set the random seed for reproducibility `np.random.seed(0)`
- Display the first few rows of the dataset
- Look at the dataset columns and their data types using `info()`

## Level 1: Variable Identification Protocol
- Get a statistical summary of the anonymized features using `describe()`
- Plot the distribution of the hidden features using `subplots()` and `hist()` which gives the first hidden feature *age*
- Create a new column `grade` which is the average of the `G1`, `G2`, and `G3` columns
- Plot the `grades` and `faliures` vs `Feature_2` which gives us the second hidden feature *study_time*
- Plot the `grades` and `failures` vs `Feature_3` which gives us the third hidden feature *stress_levels*

## Level 2: Data Integrity Audit
- Check the number of `object` columns having missing values
- Fill the missing values in `object` columns with `mode()` or preserving the original ratio of values as in the `groupby` object of `romantic` column. Use the technique that gives the best F1 score
- Check the number of `numeric` columns having missing values
- Fill the missing values in `numeric` columns with `mean()` if it has continous values or with `mode()` if it has categorical values

## Level 3: Exploratory Insight Report
Asked the following questions and answered them using EDA techniques and visualizations:
- Does education of parents affect the `grades` of the student?
- How does relationship status and sex affect the `grades` of students? 
- How are `famrel, Dalc, goout, health, Feature_3(stress level)` associated with each other?
- How does Parental cohabitation status affect student's Alcohol consumption and Family relationship quality?
- What is the relation between Age and Relatioship Status?

## Level 4: Relationship Prediction Model
- Converted the categorical variables into numerical using `map()`
- Prepared the new dataframe by dropping some features to increase the model performance.<br> Dropped features: `school, famsize, Fedu, Medu, guardian, Mjob, Fjob, nursery, higher, address, freetime, health, famsup, reason, Feature_2, absences, activities, paid, schoolsup`
- Performed `train_test_split()` to split the data into training and testing sets
- Used `StandardScaler()` to scale the data
- Built multiple classifiers: `Logistic Regression`, `Random Forest`, `Decision Tree`, `KNN` and `XGBoost`
- Choose the best model based on the F1 score and accuracy : `Logistic Regression`

## Level 5: Model Reasoning and Interpretation
- Plotted the 2D decision boundary of the best model using `meshgrid()` and the features `goout` and `Feature_3`(stress levels)
- Used `SHAP` to interpret the best model and understand the impact of features on the predictions
- Generated local explanations for two students one predicted `yes` and one predicted `no` for the best model
- Interpreted the results and found what drives the model's predictions. Made a interpretation report of the results

## Bonus Level: Boundary Match
- Identified the algorithm that produced the decision boundary plot from visual clues like linearity, complexity and shape of the decision boundary and explained the reasoning
- The answers are in the `Bonus Level` section of the notebook

