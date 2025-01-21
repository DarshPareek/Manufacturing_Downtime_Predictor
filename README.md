# Predictive Analysis for Manufacturing Operations

This project provides a RESTful API for predicting machine downtime or production defects using a Logistic Regression model. The API allows users to upload manufacturing data, train the model, and make predictions.
## Table of Contents
- Features
- Prerequisites
- Setup
- API Endpoints
- Usage
- Example Workflow
- Folder Structure
- Dependencies
- License

## Features
- Upload CSV Data: Upload manufacturing data in CSV format.
- Train Model: Train a Logistic Regression model on the uploaded data.
- Make Predictions: Predict machine downtime or production defects based on input features.
- Visualize Data: Plot the decision boundary of the Logistic Regression model (optional).

## Prerequisites
Before running the project, ensure you have the following installed:
- Python 3.8 or higher
- pip (Python package manager)

Setup
1. Clone the Repository:
    ```bash
    Copy

    git clone https://github.com/your-username/Predictive-Manufacturing-API.git
    cd Predictive-Manufacturing-API
    ```
2. Install Dependencies:
    Install the required Python packages using the requirements.txt file:
    ```bash
    Copy

    pip install -r requirements.txt
    ```
3. Run the Flask Server:
    Start the Flask server by running:
    ```bash
    Copy

    python app.py
    ```
    The server will start at http://127.0.0.1:5000/.

## API Endpoints
1. Root Endpoint
- URL: /
- Method: GET
- Description: Welcome message for the API.
- Example Response:
    ```json
    Copy

    "Welcome to the Manufacturing Predictive Analysis API!"
    ```
2. Upload Endpoint
- URL: /upload
- Method: POST
- Description: Upload a CSV file containing manufacturing data.
- Request Format: Form-data with a file field named file.
- Example Request:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/upload -F "file=@data/manufacturing_data.csv"
    ```
- Example Response:
    ```json
    Copy

    {
        "message": "File 'manufacturing_data.csv' uploaded and data loaded successfully!"
    }
    ```
3. Train Endpoint
- URL: /train
- Method: POST
- Description: Train the Logistic Regression model on the uploaded data.
- Example Request:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/train
    ```
- Example Response:
    ```json
    Copy

    {
        "message": "Model trained and saved successfully!"
    }
    ```
4. Predict Endpoint
- URL: /predict
- Method: POST
- Description: Make a prediction based on input features (Temperature and Run_Time).
- Request Format: JSON.
- Example Request:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/predict \
    -H "Content-Type: application/json" \
    -d '{"Temperature": 85, "Run_Time": 120}'
    ```
- Example Response:
    ```json
    Copy

    {
        "Downtime": "Yes",
        "Confidence": 0.85
    }
    ```
## Usage
Step 1: Upload Data

Upload a CSV file containing manufacturing data using the /upload endpoint.

Step 2: Train the Model

Train the Logistic Regression model using the /train endpoint.

Step 3: Make Predictions

Use the /predict endpoint to make predictions based on input features.

Example Workflow

    Upload Data:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/upload -F "file=@data/manufacturing_data.csv"
    ```
    Train the Model:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/train
    ```
    Make a Prediction:
    ```bash
    Copy

    curl -X POST http://127.0.0.1:5000/predict \
    -H "Content-Type: application/json" \
    -d '{"Temperature": 85, "Run_Time": 120}'
    ```
## Folder Structure
```Copy

Predictive-Manufacturing-API/
│
├── app.py                # Flask application
├── model.py              # Logistic Regression model
├── logistic_regression_model.pkl  # Trained model file
├── uploads/              # Folder for uploaded CSV files
│   └── manufacturing_data.csv
├── data/                 # Folder for sample datasets
│   └── manufacturing_data.csv
├── requirements.txt      # Dependencies
└── README.md             # Documentation
```
## Dependencies

The project uses the following Python packages:
- Flask
- scikit-learn
- pandas
- numpy
- matplotlib
- joblib

Install the dependencies using:
```bash
Copy

pip install -r requirements.txt
```
