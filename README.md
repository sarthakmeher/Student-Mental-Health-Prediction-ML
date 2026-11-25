# Student Mental Health Prediction
A machine learning application that estimates a student mental health score (0–10) from lifestyle, academic, stress, and social-media usage information. The project combines a trained regression model, a FastAPI prediction service, and a lightweight web interface.
Important: This project is for educational and informational purposes only. Its output is not a medical diagnosis, clinical assessment, or substitute for professional mental-health support.

# Live Application
- Web application: https://student-mental-health-prediction-ml.onrender.com
- GitHub repository: https://github.com/sarthakmeher/Student-Mental-Health-Prediction-ML
The frontend JavaScript in this repository is configured to send prediction requests to the deployed API URL above.
# Project Overview
The model uses information about a student's profile and daily routine to predict a numerical mental-health score. The input features include:
- Age, gender, country, and academic level
- Most-used social-media platform and primary purpose of use
- Average daily social-media usage hours and daily phone unlocks
- Study hours, physical activity hours, and sleep hours per night
- Self-reported stress level
The notebook loads a dataset named Student_Social_Media_And_Mental_Health_Impact.csv and performs data inspection, preprocessing, model training, hyperparameter tuning, and evaluation.
# Key Features
- Interactive web form: Collects student profile, academic, digital-habit, and lifestyle information.
- Input validation: Checks required fields and numeric ranges before submitting a prediction.
- Machine learning inference: Uses a saved scikit-learn regression pipeline to estimate the score.
- REST API: Exposes a FastAPI /predict endpoint.
- Prediction visualization: Displays the predicted score on a 0–10 gauge with a descriptive signal band.
- Reusable trained model: Loads Mental_Health_Model.pkl for inference.
  
# Technology Stack

| Technology | Purpose |
|---|---|
| Python | Model development, training, and prediction |
| Pandas | Data loading, cleaning, and manipulation |
| NumPy | Numerical computations and array operations |
| Scikit-learn | Machine learning model development and evaluation |
| Random Forest Regressor | Predicting student mental health scores |
| Linear Regression | Baseline regression model for comparison |
| Matplotlib | Data visualization and exploratory data analysis |
| Joblib | Saving and loading the trained ML model |
| FastAPI | Building REST API for model predictions |
| Uvicorn | Running the FastAPI backend server |
| Pydantic | API request validation and data handling |
| HTML | Structuring the web application |
| CSS | Styling and designing the user interface |
| JavaScript | Frontend interactions and API integration |
| Jupyter Notebook | Exploratory data analysis, preprocessing, model training, and evaluation |

# Machine Learning Workflow
1. Data loading: Read the student social-media and mental-health dataset.
2. Exploratory data analysis: Inspect dataset dimensions, columns, missing values, duplicates, and feature distributions.
3. Preprocessing: Apply feature-specific transformations to numerical and categorical columns.
4. Model training: Train and compare Linear Regression and Random Forest regression models.
5. Hyperparameter tuning: Use RandomizedSearchCV with 5-fold cross-validation for the Random Forest pipeline.
6. Evaluation: Compare models using R², Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE).
7. Model saving: Persist the trained pipeline with Joblib for use by the API.

# Model Performance Evaluation

The following results were obtained during model evaluation on the test dataset:

| Model | Test R² | Test MAE | Test RMSE |
|---|---:|---:|---:|
| Linear Regression | 0.7398 | 0.5362 | 0.6760 |
| Random Forest (Default) | 0.8772 | 0.3478 | 0.4644 |
| Random Forest (Tuned) | 0.8652 | 0.3689 | 0.4867 |

The Default Random Forest model achieved the highest test R² score of 0.8772 among the three evaluated models.

The Tuned Random Forest model was selected and saved as `Mental_Health_Model.pkl`, which is loaded by the FastAPI backend for making predictions.


# Repository Structure

```text
Student-Mental-Health-Prediction-ML/
│
├── ML_Project.ipynb
│   └── Data analysis, preprocessing, model training, and evaluation
│
├── Mental_Health_Model.pkl
│   └── Saved trained machine learning pipeline
│
├── ml.py
│   └── FastAPI backend and prediction endpoint
│
├── main.py
│   └── Python application entry point
│
├── index.html
│   └── Web application interface
│
├── style.css
│   └── Frontend styling
│
├── script.js
│   └── Form handling and API integration
│
├── requirements.txt
│   └── Python dependencies
│
├── pyproject.toml
│   └── Project metadata and dependencies
│
├── .python-version
│   └── Python version configuration
│
├── uv.lock
│   └── Dependency lock file
│
└── .gitignore
    └── Git ignored files and directories
```

Getting Started
1. Clone the repository
git clone https://github.com/sarthakmeher/Student-Mental-Health-Prediction-ML.git
cd Student-Mental-Health-Prediction-ML
2. Create and activate a virtual environment
Windows PowerShell:
python -m venv .venv
.venv\Scripts\Activate.ps1
macOS / Linux:
python3 -m venv .venv
source .venv/bin/activate
Use a Python version compatible with the project configuration (>=3.12,<3.14).
3. Install dependencies
python -m pip install --upgrade pip
pip install -r requirements.txt
4. Run the FastAPI backend
Make sure Mental_Health_Model.pkl is in the project root, then run:
uvicorn ml:app --reload --host 127.0.0.1 --port 8000
The API will be available at:
- API root: http://127.0.0.1:8000/
- Interactive API documentation: http://127.0.0.1:8000/docs
5. Run the frontend locally
Open index.html using a local development server, such as the VS Code Live Server extension.


The notebook's inspected dataset contains 5,000 rows and 13 columns, including the target column Mental_Health_Score.
Notes and Limitations
- The prediction is an estimate learned from the dataset, not a validated mental-health screening instrument.
- Model performance depends on the source data and may not generalize to every student or population.
- Do not use the score to make medical, academic, or other high-impact decisions.
- The API loads the model file from the working directory; run Uvicorn from the repository root unless you update the model path.
- The frontend's deployed API URL may depend on the availability of the hosting service.
Future Improvements
- Add automated tests for API input validation and prediction responses.
- Add model versioning and a reproducible training pipeline.
- Improve monitoring and error handling for deployed inference.
- Document dataset provenance, licensing, and limitations.
- Add accessible explanations of the factors associated with predictions.
Author
Sarthak Meher
- GitHub: https://github.com/sarthakmeher
- Project: https://github.com/sarthakmeher/Student-Mental-Health-Prediction-ML
  
If you find this project useful, consider giving the repository a ⭐.
