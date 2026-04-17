# Flight Price Prediction

## Project Overview
This project aims to predict flight prices for various routes using historical data. The model leverages machine learning algorithms to analyze features and trends in flight pricing, enabling users to make informed decisions when booking flights.

## Features
- **Real-time Price Prediction:** Users can input flight details to receive an estimated price.
- **Data Visualization:** Includes visualizations to help understand pricing trends and factors affecting prices.
- **User-Friendly Interface:** Simple command-line interface for ease of use.
- **Customizable Models:** Users have the option to modify model parameters.

## Data Processing
The dataset contains historical flight price information, including:
- Flight routes
- Departure and arrival times
- Duration
- Airline
- Price

### Steps Taken in Data Processing:
1. **Data Cleaning:** Removed duplicates and invalid entries.
2. **Feature Engineering:** Created new features based on existing ones (e.g., day of the week, month).
3. **Data Normalization:** Scaled numerical features to improve model performance.

## Model Implementation
The model is implemented using [scikit-learn](https://scikit-learn.org/) and follows these steps:
1. **Data Splitting:** Data is divided into training and testing sets.
2. **Model Selection:** Various algorithms are explored, including Linear Regression, Decision Trees, and Random Forests.
3. **Training:** The selected model is trained on the training dataset.
4. **Evaluation:** The model's performance is evaluated on the test dataset using metrics like Mean Absolute Error (MAE) and R-squared.

## How to Use
1. **Clone the Repo:**  
   ```bash
   git clone https://github.com/[OWNER]/Flight-price-prediction.git
   cd Flight-price-prediction

### Install Dependencies: (bash)
pip install -r requirements.txt

### Run the Predictor: (bash)
python predictor.py

Enter the required flight details when prompted.

###Contributing
Feel free to open issues or submit pull requests. Contributions are welcome to improve the model and features.
