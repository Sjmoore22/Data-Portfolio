# Data Analyst Portfolio

## 📌 Overview
This repository showcases data analytics, visualization, and machine learning projects, with a focus on sports analytics, business intelligence, and data engineering.

## 📂 Repository Structure
/data-portfolio/ 
│── projects/ │ 
├── project-1/ │
│ ├── data/          # Raw and processed datasets 
│ │ ├── notebooks/   # Jupyter/Deepnote notebooks 
│ │ ├── scripts/     # Python/SQL scripts 
│ │ ├── dashboards/  # Power BI/Tableau files or links 
│ │ ├── README.md    # Project description 
│ ├── project-2/ 
│── images/ # Visualizations and screenshots 
│── README.md # Main portfolio overview 
│── LICENSE # Open-source licensing 
│── .gitignore # Ignore unnecessary files

## **Step 2: Document Portfolio Projects**
1. Create a `README.md` in the root directory with:
   - Overview of portfolio goals.
   - Links to featured projects.
   - Contact details (LinkedIn, website, etc.).
2. For each project, create a `README.md` inside its folder detailing:
   - Project objective.
   - Dataset details.
   - Tools used (Python, SQL, Power BI, etc.).
   - Key insights and results.
   - Links to dashboards or interactive reports.

## **Step 3: Develop a Sports Analytics Project in Deepnote**
1. Create a Deepnote notebook for **Golf Performance Prediction**.
2. Include:
   - **Data Import & Cleaning:** Load golf tournament dataset.
   - **Exploratory Data Analysis (EDA):** Visualizations and feature correlation.
   - **Regression Model:** Train a model to predict player performance.
   - **Results & Insights:** Identify key performance drivers.
3. Save the notebook and link it to GitHub.

### 📌 Golf Performance Analysis - Deepnote Notebook
```python
# Golf Performance Prediction - Deepnote Notebook

## 📌 Objective
# This notebook analyzes golf player performance using historical tournament data.
# It applies exploratory data analysis (EDA) and regression modeling to predict performance.

## 🛠 Tools Used
# - pandas, numpy: Data manipulation
# - seaborn, matplotlib: Data visualization
# - scikit-learn: Machine learning
# - Deepnote: Interactive execution

# Importing Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Load Dataset (Replace with actual dataset path or import method)
data = pd.read_csv("golf_tournament_data.csv")

# Display first few rows
data.head()

## 📊 Exploratory Data Analysis
# Check missing values
data.isnull().sum()

# Summary statistics
data.describe()

# Visualizing correlation between features
plt.figure(figsize=(10,6))
sns.heatmap(data.corr(), annot=True, cmap='coolwarm', fmt='.2f')
plt.title("Feature Correlation Heatmap")
plt.show()

## 🔍 Feature Selection & Data Preparation
# Selecting relevant features for performance prediction
features = ['driving_accuracy', 'greens_in_regulation', 'putts_per_round', 'scrambling']
target = 'final_score'

X = data[features]
y = data[target]

# Splitting the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

## 🏌️‍♂️ Regression Model for Performance Prediction
# Initialize and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Predictions
y_pred = model.predict(X_test)

# Model evaluation
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)
print(f"Mean Squared Error: {mse:.2f}")
print(f"R-squared Score: {r2:.2f}")
