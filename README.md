# house_price_prediction   : https://housepriceprediction-fdizxagyjnf62tacf6vfgt.streamlit.app/
An end-to-end Machine Learning project that predicts house prices using property features such as location, total square footage, number of bathrooms, and BHK configuration. The project includes data cleaning, feature engineering, model comparison, hyperparameter tuning, and deployment using Streamlit.

📌  Problem Statement
Accurate house price estimation is critical for buyers, sellers, and real estate platforms.
The goal of this project is to build a machine learning model capable of predicting house prices based on key property attributes.

📂  Dataset Overview
📊 13,000+ property records
📍 Multiple locations
🏠 Residential property data
| Feature    | Description                |
| ---------- | -------------------------- |
| location   | Area of property           |
| total_sqft | Total square footage       |
| bath       | Number of bathrooms        |
| bhk        | Number of bedrooms         |
| price      | Target variable (in Lakhs) |

🧹  Data Preprocessing
✔ Data Cleaning
Removed duplicate records
Handled missing values
Removed invalid sqft entries
Treated extreme outliers

✔ Feature Engineering
Created a new feature:
df["price_per_sqft"] = (df["price"] * 100000) / df["total_sqft"]
🔹 Why?
To normalize pricing across properties and detect abnormal valuations.

Handled Outliers
Handling outliers in total_sqft
Note: here there are some houses with less than 300 sqft (ouliers)
formula:  total_sqft/bhk >=300  #to keep only realistic rows
handling outliers in BHK
Handling outliers in bath column
Realistic ---> no.of.bath<bhk+2
 1bhk ---> 2
 2bhk ---> 3
 3bhk ---> 5

unrealistic
1bhk  ---> 4 bath
2bhk  ---> 5 bath

bath<bhk+2  to keep realistic bath counts
Handling outliers in price per sqft
IQR method --->outlier handling method

🤖  Model Development
 Linear Regression
Training R²: 0.8668
Testing R²: 0.8002


 Random Forest Regression
Training R²: 0.8886
Testing R²: 0.8170

Random Forest performed better than Linear Regression.

⚙️  Hyperparameter Tuning (GridSearchCV)
Best Parameters:
{'max_depth': 6, 'n_estimators': 200}

Final Performance:
Best CV Score: 0.8333
Training R²: 0.8878
Testing R²: 0.8180
Final R²: 0.8180
MAE: 14.94 Lakhs

📊  Model Performance Summary
Model	Train R²	Test R²
Linear Regression	0.8668	0.8002
Random Forest	0.8886	0.8170
Tuned Random Forest	0.8878	0.8180

🏆 Final Model Selected: Tuned Random Forest

🚀  Deployment – Streamlit App
Key Features:
Location dropdown
BHK selection
Bathroom selection
Total Sqft input
Real-time price prediction
INR formatted output

🛠  Tech Stack

Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
Streamlit
Pickle

📈  Key Achievements

✔ Built complete ML pipeline
✔ Engineered price_per_sqft feature
✔ Performed location-based outlier removal
✔ Improved generalization using GridSearchCV
✔ Achieved 81.8% R² on unseen data
✔ Deployed production-ready ML application
