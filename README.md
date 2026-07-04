Smart Hospital Resource Allocation and Triage Dashboard using various machine learning techniques. Here's a summary of the key steps and models implemented:

Data Loading and Preprocessing: The project begins by loading train_clean.csv and test_clean.csv datasets. A ColumnTransformer is used for preprocessing, applying StandardScaler to numerical features (age, number of procedures, comorbidity score) and OneHotEncoder to categorical features (gender, primary diagnosis, discharge to). This prepared data is then split into training and validation sets for both classification and regression tasks.

Classification Models:

A Logistic Regression model is trained to predict patient readmission, with performance evaluated using a classification report.
A K-Nearest Neighbors (KNN) model is also trained for classification.
A Decision Tree Classifier is implemented, and its decision logic is visualized as a clinical triage decision matrix strategy.
Regression Models:

A Linear Regression model is established as a baseline for predicting days_in_hospital.
A Random Forest Regressor is trained, and its R² score is then improved through hyperparameter tuning using RandomizedSearchCV.
Data Exploration:

K-Means Clustering is applied to group patients based on their clinical metrics, visualizing hospital resource consumption cohorts.
Principal Component Analysis (PCA) is used for dimensionality reduction, mapping the readmission space and showing the variance captured by the principal components.
Prediction and Export: Final readmission predictions and probabilities are generated on the test data using the Logistic Regression model and exported to hospital_resource_predictions.csv.

ML Model Serialization: All trained machine learning components (preprocessor, Logistic Regression model, regression transformer, and Random Forest Regressor model) are serialized using joblib for persistent storage and later use in the application.

Full-Stack Application Development:

A FastAPI backend (backend_app.py) is created to serve two prediction endpoints: /predict_readmission and /forecast_stay. This API loads the serialized ML models to provide real-time inference.
A Streamlit frontend (frontend_app.py) is built to serve as an interactive dashboard. This dashboard allows users to input patient clinical parameters and receive predictions from the FastAPI backend regarding readmission risk and forecasted length of stay, alongside visualizations for patient placement and resource constraints.
Deployment: The FastAPI backend is launched locally in a background thread, and the Streamlit dashboard is exposed publicly using ngrok to provide a functional and accessible web application.


portal: https://smugly-salt-plaster.ngrok-free.dev
