# Employee Churn Prediction ML Model
**RandomForestClassifier_ML_Employee Churn Prediction Model**

This project demonstrates a machine learning pipeline to predict employee churn using data from Google Cloud's BigQuery. The process involves connecting to BigQuery, retrieving data, building and training a machine learning model using PyCaret, making predictions, and writing the results back to BigQuery.

## Workflow Overview

1. **Authentication and BigQuery Client Initialization**
   - **Libraries Required**: `google.cloud.bigquery` for BigQuery access and `google.colab` for authentication within a Colab environment.
   - **Authentication**: Uses `auth.authenticate_user()` for Google Cloud resource access.
   - **Client Initialization**: Initializes a BigQuery client with a specified project ID and location to interact with BigQuery datasets and tables.

2. **Data Retrieval**
   - **Dataset and Table References**: References are set up for a dataset (`employeedata`) and two tables (`tbl_hr_data` and `tbl_new_employees`) within this dataset.
   - **Schema Viewing**: Retrieves the schema of the tables to understand data structure (e.g., column names, data types).
   - **Data Conversion to DataFrame**: Fetches data from both tables and converts them into Pandas dataframes (`df` and `df2`) for analysis and modeling.

3. **Building the Model with PyCaret (RandomForestClassifier)**
   - **PyCaret Installation**: Installs PyCaret, an automated machine learning library.
   - **Model Setup**: Prepares `df` for modeling with PyCaret, specifying the target variable (`Quit_the_Company`), session ID, ignored features, and categorical features.
   - **Model Training**: Compares various models using `compare_models()` and trains a random forest model (`rf`) using `create_model('rf')`.
   - **Model Prediction**: Makes predictions on both the original data (`df`) and new data (`df2`), storing results in `final_df` and `new_predictions`, respectively.

4. **Writing Results Back to BigQuery**
   - **BigQuery Writeback**: Writes the predictions for new employees (`new_predictions`) back to BigQuery into a table named `employeedata.pilot_predictions`, replacing it if it exists.
   - **Feature Importance**: Extracts feature importance from the random forest model, converts it into a dataframe (`feature_table`), and writes it back to BigQuery in a table called `employeedata.feature_table`.

## Outcome

- The code successfully connects to BigQuery, retrieves employee data, trains a model to predict whether employees will quit the company, makes predictions on both existing and new employee data, and stores these predictions and feature importance analysis back in BigQuery.
- The data used includes:
  - **HR Data (`tbl_hr_data.csv`)**: Used for model training.
  - **New Employee Data (`tbl_new_employees.csv`)**: Used for making predictions with the trained model.

## Key Files
- `tbl_hr_data.csv`: HR data used for training the model.
- `tbl_new_employees.csv`: New employee data used for prediction.

## Usage

To run this code:

1. Ensure you have access to Google Cloud's BigQuery and the necessary permissions to read and write data.
2. Run each step of the workflow in a Colab environment to authenticate, retrieve data, train the model, make predictions, and write results back to BigQuery.

## Future Enhancements

- **Automate the Workflow**: Set up a scheduled pipeline to automate data retrieval, model training, and prediction updates.
- **Enhanced Model Tuning**: Experiment with other models and hyperparameters for potentially better prediction accuracy.
- **Add More Features**: Incorporate additional employee data for a more robust churn prediction model.

This workflow demonstrates a complete data science pipeline, from data retrieval, preprocessing, model building, and evaluation, to deploying the model's predictions and insights back into a data warehouse (BigQuery) for further analysis or operational use.

