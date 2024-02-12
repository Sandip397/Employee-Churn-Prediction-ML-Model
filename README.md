# Employee-Churn-Prediction-ML-Model
RandomForestClassifier_ML_Employee Churn Prediction Model

The provided code outlines a process for connecting to Google Cloud's BigQuery service from a Colab environment, retrieving data from specific BigQuery tables, converting this data to Pandas dataframes, using PyCaret to build and train a machine learning model, making predictions with this model, and finally, writing results back to BigQuery. Here's a step-by-step explanation and the outcomes expected from each step:

Authentication and BigQuery Client Initialization
•	Libraries Required: google.cloud.bigquery for BigQuery access and google.colab for authentication within a Colab environment.
•	Authentication: The user is authenticated using auth.authenticate_user(), which is necessary for accessing Google Cloud resources.
•	Client Initialization: A BigQuery client is initialized with a specific project ID and location. This client is used to interact with BigQuery datasets and 
    tables.

Data Retrieval
•	Dataset and Table References: References to a specific dataset ('employeedata') and two tables within this dataset ('tbl_hr_data' and 'tbl_new_employees') are 
    created.
•	Schema Viewing: The schema of the tables is retrieved to understand the structure of the data (e.g., column names, data types).
•	Data Conversion to Dataframe: The data from both tables is fetched and converted into Pandas dataframes (df and df2) for analysis and modeling.

Building the Model with PyCaret(RandomForestClassifier) 
•	PyCaret Installation: PyCaret, an automated machine learning library, is installed using pip.
•	Model Setup: The dataframe df is prepared for modeling with PyCaret, specifying a target variable ('Quit_the_Company'), a session ID, features to ignore, and 
    categorical features.
•	Model Training: Various models are compared using compare_models(), and a random forest model ('rf') is created with create_model('rf').
•	Model Prediction: Predictions are made on the original data (df) and new data (df2), and the results are stored in final_df and new_predictions, respectively.

Writing Results Back to BigQuery
•	BigQuery Writeback: The predictions for new employees (new_predictions) are written back to BigQuery into a table named 'employeedata.pilot_predictions', 
    replacing it if it exists.
•	Feature Importance: The feature importance is extracted from the random forest model, converted into a dataframe (feature_table), and written back to BigQuery 
    in a table called 'employeedata.feature_table'.

Outcome
•	The code successfully connects to BigQuery, retrieves employee data, trains a model to predict whether employees will quit the company, makes predictions on 
    both existing and new employee data, and stores these predictions and the feature importance analysis back in BigQuery.
•	The data used includes HR data (tbl_hr_data.csv) for model training and new employee data (tbl_new_employees.csv) for making predictions with the trained model.

This workflow demonstrates a complete data science pipeline from data retrieval, preprocessing, model building and evaluation, to deploying the model's predictions and insights back into a data warehouse (BigQuery) for further analysis or operational use.
