# Car Price Prediction using Machine Learning

## Project Overview

This project focuses on predicting the selling price of used cars using Machine Learning techniques. The project follows a complete Data Science workflow, starting from data understanding and exploratory data analysis to data preprocessing, feature engineering, model training, evaluation, and price prediction.

The main objective is to develop regression models that can learn the relationship between different car characteristics and their selling prices.

The project uses Python libraries such as **Pandas, NumPy, Matplotlib, Seaborn, and Scikit-learn**.

---

## Problem Statement

The price of a used car depends on several factors, including its current price, age, kilometers driven, fuel type, transmission type, and number of previous owners.

Estimating an appropriate selling price manually can be difficult because multiple factors influence the final price.

This project uses Machine Learning regression techniques to predict the selling price of a car based on its available features.

---

## Objectives

The main objectives of this project are:

- Understand and analyze the car price dataset.
- Perform data cleaning and preprocessing.
- Explore relationships between car features and selling price.
- Identify and handle skewed numerical features where appropriate.
- Perform feature engineering by creating a car-age feature.
- Encode categorical variables.
- Scale numerical features.
- Train different regression models.
- Compare model performance using appropriate evaluation metrics.
- Identify important features affecting car prices.
- Predict the selling price of a new car.

---

## Dataset

The dataset contains information about used cars and their selling prices.

### Main Features

| Feature | Description |
|---|---|
| `Car_Name` | Name of the car |
| `Year` | Manufacturing year |
| `Selling_Price` | Selling price of the car (Target) |
| `Present_Price` | Current/ex-showroom price |
| `Driven_kms` | Number of kilometers driven |
| `Fuel_Type` | Fuel type of the car |
| `Selling_type` | Dealer or individual seller |
| `Transmission` | Manual or automatic |
| `Owner` | Number of previous owners |

The target variable of the project is:

**`Selling_Price`**

Since the target is a continuous numerical value, this is a **regression problem**.

---

## Dataset Source

The dataset was obtained from Kaggle:

**Car Data / Car Price Prediction Dataset**

The dataset used in this project is provided as `car data.csv`.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook / Google Colab

---

## Project Workflow

The project follows these major steps:

```text
Dataset
   ↓
Data Understanding
   ↓
Data Cleaning
   ↓
Exploratory Data Analysis
   ↓
Feature Engineering
   ↓
Skewness Analysis
   ↓
Data Transformation
   ↓
Feature Selection
   ↓
Train-Test Split
   ↓
Encoding & Scaling
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Model Comparison
   ↓
Feature Importance
   ↓
New Car Price Prediction
```

---

## 1. Data Loading and Understanding

The dataset is loaded using Pandas. Initial analysis is performed to understand:

- Number of rows and columns
- Data types
- Missing values
- Duplicate records
- Numerical statistics
- Categorical values

---

## 2. Data Cleaning

The dataset is checked for missing values and duplicate records.

The `Car_Name` column is removed before model training because it contains individual car names and is not required for the main numerical prediction task.

---

## 3. Exploratory Data Analysis

Exploratory Data Analysis is performed to understand the distribution and relationships within the dataset.

The analysis includes:

- Numerical feature distributions
- Boxplots for detecting potential outliers
- Correlation analysis
- Scatterplots
- Categorical feature analysis
- Relationship between car features and selling price

The EDA helps understand which variables may have a strong relationship with the target variable.

---

## 4. Feature Engineering

A new feature called `Car_Age` is created from the manufacturing year.

```python
Car_Age = Current_Year - Year
```

This provides a more meaningful representation of vehicle age than using the manufacturing year directly.

After creating `Car_Age`, the original `Year` feature can be removed.

---

## 5. Skewness Analysis and Transformation

The numerical variables are checked for skewness.

Some features show strong right-skewed distributions, particularly:

- `Driven_kms`
- `Present_Price`
- `Car_Age`
- `Owner`

Log transformation is tested using:

```python
np.log1p()
```

The transformation is not blindly applied to every feature. Features are evaluated before and after transformation.

For example, `Present_Price` showed a substantial improvement in skewness after transformation.

This approach ensures that transformation is applied only where it provides a meaningful improvement.

---

## 6. Feature Selection

The `Car_Name` feature is removed because it contains many unique categorical values and is not necessary for the selected prediction approach.

The remaining useful features include:

- `Present_Price`
- `Driven_kms`
- `Fuel_Type`
- `Selling_type`
- `Transmission`
- `Owner`
- `Car_Age`

These features are used to predict `Selling_Price`.

---

## 7. Data Preprocessing

The dataset contains both numerical and categorical features.

### Numerical Features

Numerical features are standardized using:

```python
StandardScaler
```

### Categorical Features

Categorical features are converted into numerical representations using:

```python
OneHotEncoder
```

A `ColumnTransformer` is used to apply the appropriate preprocessing technique to each type of feature.

---

## 8. Train-Test Split

The dataset is divided into training and testing sets.

```text
80% → Training Data
20% → Testing Data
```

The training data is used to train the models, while the testing data is used to evaluate their performance on unseen data.

---

## 9. Machine Learning Models

Three regression algorithms are considered:

### Linear Regression

Linear Regression provides a simple baseline model and attempts to model the relationship between the input features and selling price using a linear relationship.

### Decision Tree Regression

Decision Tree Regression can capture nonlinear relationships between car characteristics and selling price.

### Random Forest Regression

Random Forest combines multiple decision trees to produce a more robust prediction.

It is particularly useful when relationships between features and the target are nonlinear.

---

## 10. Model Evaluation

The models are evaluated using three common regression metrics.

### Mean Absolute Error (MAE)

MAE measures the average absolute difference between actual and predicted prices.

**Lower MAE is better.**

### Root Mean Squared Error (RMSE)

RMSE gives greater importance to larger prediction errors.

**Lower RMSE is better.**

### R² Score

R² indicates how much of the variation in the target variable is explained by the model.

**Higher R² is better.**

The models are compared using all three metrics to select the best-performing model.

---

## 11. Feature Importance

Feature importance is analyzed using the Random Forest model.

This helps determine which variables contribute most to the prediction of car selling prices.

The feature-importance analysis provides useful information for understanding the factors that influence used-car prices.

---

## 12. New Car Price Prediction

After selecting the best-performing model, it can be used to predict the selling price of a new car.

For example, information such as:

- Present price
- Kilometers driven
- Fuel type
- Selling type
- Transmission
- Number of previous owners
- Car age

can be provided to the trained model to estimate its expected selling price.

---

## Results

The performance of the trained models is compared using:

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Linear Regression | To be filled | To be filled | To be filled |
| Decision Tree Regression | To be filled | To be filled | To be filled |
| Random Forest Regression | To be filled | To be filled | To be filled |

The model with the **lowest MAE and RMSE and highest R² score** is selected as the final model.

---

## Key Insights

The project provides several useful insights into used-car price prediction:

- The present/current price of a vehicle is an important factor in estimating its selling price.
- Vehicle age can provide useful information about depreciation.
- The number of kilometers driven can influence the value of a used vehicle.
- Fuel type and transmission type can also contribute to price differences.
- Previous ownership history provides additional information about the condition and market value of a vehicle.
- Machine Learning can be used to estimate prices and support better buying and selling decisions.

---

## Real-World Applications

A car price prediction system can be useful for:

- Used-car dealerships
- Individual car sellers
- Car buyers
- Online automobile marketplaces
- Vehicle valuation systems
- Financial and insurance analysis

Such systems can provide an estimated market price and help users make more informed decisions.

---

## Project Structure

```text
Car-Price-Prediction/
│
├── data/
│   └── car data.csv
│
├── notebooks/
│   └── Car_Price_Prediction.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/Car-Price-Prediction.git
```

Move into the project directory:

```bash
cd Car-Price-Prediction
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook
```

Then open:

```text
notebooks/Car_Price_Prediction.ipynb
```

---

## Requirements

The main Python libraries required for this project are:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

## Conclusion

This project demonstrates a complete Data Science workflow for predicting used-car prices. Starting from raw data, the project performs data exploration, cleaning, feature engineering, skewness analysis, transformation, feature selection, preprocessing, model training, and evaluation.

Different regression models are compared to determine which approach provides the most accurate predictions. The project also demonstrates how Machine Learning can be applied to a practical business problem such as vehicle price estimation.

Overall, this project provides practical experience with **Data Analysis, Data Preprocessing, Feature Engineering, Exploratory Data Analysis, Regression, Model Evaluation, and Machine Learning-based Prediction**.                                
