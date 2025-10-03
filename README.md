## End to End Machine Learning Project

## Student Performance Analysis

## Overview

This project aims to predict student performance based on various input features using machine learning techniques. It includes data preprocessing, model building, and a Flask-based web interface for making predictions.

## Project Structure

```
/Users/AzanAnsari/DsProjects/mlproject/
├── app.py                # Flask application for serving predictions
├── readme.md             # Project documentation
├── requirements.txt      # Project dependencies
├── src
│   ├── components        # Data ingestion and transformation components
│   ├── pipeline          # Training and prediction pipelines
│   └── utils             # Utility functions
├── templates             # HTML templates for the web interface
│   └── home.html         # Home page for inputting data and displaying results
```

## Dependencies

To run this project, you need to install the following dependencies:

```bash
pip install -r requirements.txt
```

The `requirements.txt` file includes the following libraries:

- pandas
- numpy
- seaborn
- scikit-learn
- catboost
- xgboost
- dill
- flask
- gunicorn

## Setup and Installation

1.  **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd mlproject
    ```
2.  **Create a virtual environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Linux/macOS
    venv\Scripts\activate  # On Windows
    ```
3.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

## Running the Application

To run the Flask application, use the following command:

```bash
gunicorn --bind :8000 app:app
```

Alternatively, for local development (not recommended for production):

```bash
python app.py
```

## Project Details

### `app.py`

-   This file contains the Flask application that handles web requests, prediction logic, and rendering of HTML templates.
-   The `/` route redirects to the `/predictdata` route.
-   The `/predictdata` route handles both GET and POST requests:
    -   GET: Renders the `home.html` template.
    -   POST: Collects user input, preprocesses it, makes a prediction using the `PredictPipeline`, and displays the result.
-   Error handling is implemented to display user-friendly error messages in case of invalid input or other exceptions.

### `src/pipeline/predict_pipeline.py`

-   This file defines the `PredictPipeline` class, which encapsulates the prediction logic.
-   It also includes the `CustomData` class for handling input data.

### `templates/home.html`

-   This file contains the HTML template for the home page, which includes input fields for the features and a display area for the prediction results.

## Model Training

The model training code is not included in the provided file list. Normally, a separate script or notebook would be used to train the model and serialize it using `dill`. The trained model file would then be loaded by the `PredictPipeline` for making predictions.

## Usage

1.  Open the application in your web browser.
2.  Enter the required details in the input fields.
3.  Click the "Predict" button to get the predicted student performance.

## Improvements

-   Implement robust model training and evaluation.
-   Add more comprehensive error handling and logging.
-   Enhance the user interface with better styling and user experience.
-   Incorporate data validation and sanitization to prevent security issues.