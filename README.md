🏠 Bengaluru House Price Prediction

A beginner-friendly Machine Learning Regression project that predicts the price of a house in Bengaluru based on location, area type, availability, total square feet, number of bathrooms, balconies, and BHK.

📌 Project Overview

The goal of this project is to build a House Price Prediction model using the Bengaluru House Data dataset.

Workflow

1 Load and understand the dataset

2 Handle missing and duplicate data

3 Convert data into suitable numerical formats

4 Perform feature engineering

5 Remove price outliers

6 Split data into training and testing sets

7 Encode categorical features using One-Hot Encoding

8 Train a Linear Regression model

9 Evaluate the model using R² Score

10 Enter house details and predict the estimated price

📊 Dataset

Dataset: Bengaluru House Data

Feature:
area_type :Type of area measurement

availability : Availability status of the property

location :Location of the house

total_sqft :Total area in square feet

bath :Number of bathrooms

balcony :Number of balconies

BHK :Number of bedrooms/hall/kitchen

price :House price in Indian Rupees Lakhs

🛠️ Technologies Used

Python

Pandas

NumPy

Scikit-learn

Jupyter Notebook / Google Colab

🔄 Machine Learning Workflow

1. Data Cleaning

The dataset is checked for missing values, duplicate records, incorrect data types, and invalid values.

2. Data Conversion

total_sqft contains values such as 1133 - 1384. Range values are converted into their average.

The bath and balcony columns are converted into numerical values.

3. Feature Engineering

The size column contains values such as 2 BHK and 4 Bedroom. The numerical value is extracted into a new BHK feature, and the original size column is removed.

4. Outlier Removal

Price outliers are removed using the Interquartile Range (IQR) method.

Q1 = house['price'].quantile(0.25)
Q3 = house['price'].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

house = house[
    (house['price'] >= lower) &
    (house['price'] <= upper)
]

5. Train-Test Split

The cleaned dataset is divided into training and testing data.

X_train, X_test, Y_train, Y_test = train_test_split(
    X, Y,
    test_size=0.2,
    random_state=42
)

6. One-Hot Encoding

Categorical features such as area_type, availability, and location are converted into numerical form using One-Hot Encoding.

A ColumnTransformer is used to apply preprocessing to the required columns.

7. Model Training

The project uses Linear Regression.

lr = LinearRegression()

pipe = make_pipeline(
    column_trans,
    lr
)

pipe.fit(X_train, Y_train)

📈 Model Evaluation

The model is evaluated using the R² Score.

Y_pred = pipe.predict(X_test)

print("R2 Score:", r2_score(Y_test, Y_pred))

🔮 House Price Prediction

After training, the user can enter house details manually.

Example:

Area Type: super built up area
Availability: ready to move
Location: whitefield
Total Square Feet: 1200
Number of Bathrooms: 2
Number of Balconies: 1
Number of BHK: 2

The model then predicts the estimated house price in Lakhs.

Predicted House Price: XX.XX Lakhs

📁 Project Structure

Bengaluru-House-Price-Prediction/
│
├── Bengaluru_House_Data.csv
├── Cleaned_House_data.csv
├── House_Price_Prediction.ipynb
└── README.md

Note: If the dataset is too large for GitHub, you can upload the notebook without the CSV and provide the original dataset source separately.

🎯 Objective

This project demonstrates the basic end-to-end workflow of a Machine Learning Regression problem:

Data preprocessing

Feature engineering

Categorical data encoding

Outlier removal

Train-test splitting

Linear Regression

Model evaluation

Prediction on new house data

🚀 Future Improvements

Compare Linear Regression with other regression algorithms

Improve location preprocessing

Add more exploratory data analysis

Build a web interface for predictions

Deploy the model as a web application

Improve prediction accuracy through additional feature engineering


📜 License

This project is intended for educ
