# 📊 Project 2: Initial Analysis and Problem Selection

## 🛣️ Project Description

This project analyzes multiple datasets and develops a machine learning solution for one selected dataset.

The project follows a complete data science workflow:

- Exploratory Data Analysis (EDA)
- Data Cleaning and Preprocessing
- Feature Selection
- Machine Learning Model Development
- Hyperparameter Optimization
- Model Evaluation
- Model Export and Serialization

The final solution includes a trained classification model exported as a `.joblib` artifact for future deployment and inference.

---

## 📁 Project Structure

- `datasets/` → Contains the dataset files  
- `EDA/` → Jupyter notebooks for analysis and exploration  
- `selected_dataset/` → Selected dataset and notebook for the final analysis and model development
- `README.md` → Project documentation  

---

## 📊 Dataset

The datasets analyzed in this project are:

1. **Aircraft Registrations in Chile**

**Description**
Dataset containing information about aircraft registrations in Chile, including manufacturer, model, aircraft type, registration details, and operational characteristics.

**Potential Business Problem**
Develop a predictive model to identify aircraft types with higher commercial demand and estimate future registration trends based on historical registration patterns.

2. **Earthquakes in Chile**

**Description**
Dataset containing seismic event records in Chile, including date, time, geographic coordinates, depth, magnitude as earthquake-related attributes.

**Potential Business Problem**
Analyze historical seismic activity to identify geographic areas with higher earthquake occurrence rates and support risk assessment for infrastructure planning and investment decisions.

3. **Healthy Diet and Calorie Intake**

**Description**
Dataset containing demographic, biometric, lifestyle, and dietary information, including variables such as age, gender, height, weight, physical activity, and calorie consumption.

**Potential Business Problem**
Develop a predictive model to estimate individual calorie needs or identify nutritional risk patterns that could support preventive healthcare and personalized dietary recommendations.

4. **Maximum and Minimum Daily Temperatures in Chile**

**Description**
Dataset containing historical weather observations across Chile, including location, date, maximum temperature, minimum temperature, and related geographic information.

**Potential Business Problem**
Develop a forecasting model to predict future temperature patterns and support tourism planning by identifying the most favorable seasons to visit specific destinations.

| Dataset                         | Possible ML Task             |
| ------------------------------- | ---------------------------- |
| Aircraft Registrations in Chile          | Classification               |
| Earthquakes in Chile                     | Clustering                   |
| **Healthy Diet and Calorie Intake** | **Classification (Selected)**               |
| Maximum and Minimum Daily Temperatures in Chile              | Time series forecasting      |

---

## 📚 Initial EDA Summaries

### 1. Aircraft Registrations in Chile

- **Dataset size:** 2,010 records and 7 variables.
- **Data quality:** No missing values; only 4 duplicate records, likely related to ownership changes.
- **Main insight:** Aircraft usage is strongly associated with manufacturer and aircraft type.
- **Key patterns:**

  - Private aircraft represent 63.9% of registrations.
  - Airbus and Boeing are primarily linked to commercial operations.
  - Cessna and Piper are predominantly used for private purposes.
  - Gliders and gyrocopters are exclusively private.
- **Machine Learning potential:** Strong candidate for a **classification problem**, predicting whether an aircraft is registered for private or commercial use.

---

### 2. Earthquakes in Chile

- **Dataset size:** 4,018 records and 5 variables.
- **Data quality:** No missing values; only 3 duplicate records.
- **Time coverage:** March 2012 to May 2025.
- **Main insight:** Earthquakes are geographically distributed along Chile's seismic zones, with regional differences in depth and location.
- **Key patterns:**

  - Magnitudes are approximately normally distributed around 4.4.
  - Most seismic activity remains stable throughout the year.
  - A few extreme events exceed magnitude 8.0.
  - Depth shows a moderate relationship with geographic location.
- **Machine Learning potential:** Best suited for **clustering**, as no natural target variable exists for supervised learning.

---

### 3. Healthy Diet and Calorie Intake

- **Dataset size:** 6,000 records and 15 variables.
- **Data quality:** Generally high, although 54 records contain invalid negative carbohydrate values.
- **Main insight:** Physical activity level has a stronger relationship with health status than diet type.
- **Key patterns:**

  - Strong correlation between calorie requirements and calorie consumption (r = 0.91).
  - BMI is strongly associated with weight (r = 0.78).
  - Most outliers appear to be realistic observations.
  - Values are generally consistent with WHO health standards.
- **Machine Learning potential:** Well-suited for **classification** of health status and **regression** (optional) of calorie requirements.

---

### 4. Maximum and Minimum Daily Temperatures in Chile

- **Dataset size:** 11,870 records and 5 variables.
- **Dataset quality:** Less than 1% missing values and very few outliers.
- **Main insight:** Temperature patterns are strongly driven by seasonality.
- **Key patterns:**

  - Strong positive correlation between minimum and maximum temperatures (r = 0.66).
  - Temperature extremes are consistent with natural climate variability.
  - Geographic coverage is well balanced across weather stations.
  - Seasonal cycles are clearly visible despite weak linear relationships with time features.
- **Machine Learning potential:** Ideal for **time series forecasting**, **regression**, and climate trend analysis.

---

## 🎯 Selected Problem: 3. Healthy Diet and Calorie Intake

### Problem Description

Develop a predictive model capable of classifying an individual's **Health Status** based on biometric, dietary, and lifestyle variables such as BMI, calorie intake, nutrient consumption, age, weight, and physical activity level. The goal is to identify factors associated with healthy and unhealthy outcomes and support data-driven nutrition and wellness recommendations.

### Justification

The Healthy Diet and Calorie Intake dataset was selected because it demonstrates high data quality, with no missing values and no duplicate records, while containing a large number of observations suitable for machine learning. Exploratory analysis revealed meaningful relationships between health status and several predictor variables, particularly physical activity level, BMI, weight, and calorie consumption patterns. Although a small number of invalid carbohydrate intake values require cleaning, the dataset is generally realistic and provides strong predictive potential. Additionally, the problem has practical relevance in the fields of nutrition, preventive healthcare, and personalized wellness.

### Specific Objectives

- Clean and prepare the dataset by addressing invalid carbohydrate intake values and reviewing potential outliers.
- Analyze the influence of dietary, biometric, and lifestyle factors on health status.
- Identify the variables that contribute most significantly to predicting health outcomes.
- Develop and evaluate classification models to predict an individual's Health Status.
- Compare model performance using appropriate classification metrics.
- Generate insights that can support personalized nutrition and health recommendations.

### Selection Criteria Evaluation

- **Data quality:** Excellent, with no missing values and no duplicates.
- **Number of observations:** Sufficient for training and evaluating machine learning models.
- **Missing values:** None detected.
- **Presence of outliers:** Present but mostly represent valid observations and can provide useful information.
- **Predictive potential:** High, due to strong relationships between health status and several explanatory variables.
- **Business relevance:** High, with applications in nutrition planning, preventive healthcare, wellness programs, and personalized health recommendations.

### 🎯 Machine Learning Solution

#### Objective

Develop a multiclass classification model capable of predicting an individual's Health Status using demographic, biometric, dietary, and lifestyle variables.

#### Target Variable

`Health_Status`

Classes:

- Healthy
- Underweight
- Overweight
- Obese

### ⚙️ Machine Learning Workflow

The following steps were performed:

1. Data cleaning and validation
2. Removal of invalid observations
3. Feature engineering
4. Multicollinearity assessment (VIF)
5. Feature selection
6. Train/Test split
7. Data scaling
8. Model training
9. Hyperparameter tuning using Optuna
10. Final model evaluation
11. Model serialization using Joblib

### 🤖 Models Evaluated

The following classification algorithms were tested:

- Logistic Regression
- Decision Tree
- Random Forest
- Bagging Classifier
- XGBoost
- Tuned Logistic Regression

Performance was evaluated using:

- Accuracy
- Precision
- Recall
- F1 Score
- Confusion Matrix

### 📈 Results

The best-performing model achieved more than 90% classification accuracy on the test dataset.

Key predictors included:

- Weight
- Height
- Fat Intake

The final model demonstrated strong predictive capability across all Health Status categories.

### 💾 Trained Model

The final trained model is included in the repository as a serialized Joblib artifact.

Example:

```python
import joblib

model = joblib.load("selected_dataset/health_status_model.joblib")

prediction = model.predict(new_data)

---

## 🔧 Installation

1. Clone the repository:

```bash
git clone https://github.com/heleneInsights/data-analysis-and-problem-selection.git
```
2. Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

Open and run the Jupyter notebooks inside the `EDA/` folder to reproduce the analysis for the four initial datasets.

Open and run the Jupyter notebooks inside the `selected_dataset/` folder to reproduce the analysis for the selected dataset.

---

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Plotly
- Scikit-learn
- Optuna
- Jupyter Notebook
- Git
- GitHub

---

## 📌 Future Improvements

- Deploy the model as a web application
- Evaluate additional ensemble models
- Test performance on external datasets
- Build an API for real-time predictions

---

## ⚠️ Limitations

- The dataset may contain synthetic or simulated patterns.
- Results are limited to the available dataset.
- External validation has not yet been performed.
- Health Status definitions may be influenced by BMI-derived criteria.
- Model performance may vary when applied to real-world populations.

---

## 👤 Author

heleneInsights

---

## 🔑 License

MIT License