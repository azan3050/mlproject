# Student Performance Prediction

This project is a comprehensive machine learning application designed to predict student's math scores based on a variety of personal and academic factors. It features a full-fledged ML pipeline for data ingestion, preprocessing, model training, and evaluation, along with a Flask-based web application for interactive predictions.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
  - [Training the ML Pipeline](#training-the-ml-pipeline)
  - [Running the Web Application](#running-the-web-application)
- [Model Training and Evaluation](#model-training-and-evaluation)
- [Exploratory Data Analysis](#exploratory-data-analysis)

## Overview

The primary objective of this project is to build a robust regression model that can accurately predict a student's performance in mathematics. The prediction is based on several demographic and academic attributes, providing insights into the factors that influence student success.

## Features

- **End-to-End ML Pipeline**: A complete, automated pipeline for training and deploying the machine learning model.
- **Data Preprocessing**: Handles both numerical and categorical data with imputation, scaling, and one-hot encoding.
- **Multiple Model Evaluation**: Trains and evaluates a variety of regression models to select the best performer.
- **Web Interface**: A user-friendly web application built with Flask for easy and interactive predictions.
- **Modular Code**: Well-organized and modular code structure for better readability and maintenance.

## Technology Stack

- **Backend**: Flask, Gunicorn
- **ML Libraries**: Scikit-learn, CatBoost, XGBoost, Pandas, Numpy, dill, joblib
- **Visualization**: Seaborn, Matplotlib, Plotly

## Project Structure

The project is organized into the following directories and files:

-   `app.py`: The entry point for the Flask web application.
-   `setup.py`: The setup script for creating a distributable package of the project.
-   `requirements.txt`: A list of all Python dependencies.
-   `src/`: The main source code directory.
    -   `components/`: Core modules for the ML pipeline.
        -   `data_ingestion.py`: Handles data loading and splitting.
        -   `data_transformation.py`: Manages data preprocessing and feature engineering.
        -   `model_trainer.py`: Responsible for training and evaluating models.
    -   `pipeline/`: Scripts for managing the prediction and training pipelines.
        -   `predict_pipeline.py`: Defines the prediction logic for the web app.
    -   `exception.py`: Custom exception handling.
    -   `logger.py`: Custom logging setup.
-   `notebook/`: Jupyter notebooks for EDA and model experimentation.
-   `artifacts/`: Directory for storing output files like the trained model (`model.pkl`), preprocessor (`preprocessor.pkl`), and datasets.
-   `templates/`: HTML templates for the Flask application.

## Installation

Follow these steps to set up and run the project locally:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/mlproject.git
    cd mlproject
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

## Usage

### Training the ML Pipeline

To execute the entire machine learning pipeline, run the following command from the project root:

```bash
python src/components/data_ingestion.py
```

This script will perform data ingestion, preprocessing, model training, and save the resulting artifacts in the `artifacts/` directory.

### Running the Web Application

To launch the Flask web application for predictions:

```bash
python app.py
```

Open your web browser and go to `http://127.0.0.1:5000`. You will find a form to input student details, and the application will display the predicted math score.

## Model Training and Evaluation

The model training process involves evaluating several regression models to identify the best one for this task. The models trained include:

-   Linear Regression
-   Lasso
-   Ridge
-   K-Neighbors Regressor
-   Decision Tree
-   Random Forest Regressor
-   XGBoost Regressor
-   CatBoost Regressor
-   AdaBoost Regressor

The best model is chosen based on the R2 score. The experimental results from the notebooks indicate that **Ridge Regression** and **Linear Regression** are the top-performing models, with an R2 score of approximately **0.88**.

## Exploratory Data Analysis

The `01_eda.ipynb` notebook contains a detailed exploratory data analysis of the `StudentsPerformance.csv` dataset. The key findings from the EDA are:
- The dataset is clean with no missing values.
- The distribution of scores for math, reading, and writing are analyzed.
- The impact of various factors like gender, parental education, and lunch on student performance is visualized and discussed.