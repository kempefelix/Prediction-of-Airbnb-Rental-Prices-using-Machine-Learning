# Prediction-of-Airbnb-Rental-Prices-using-Machine-Learning
Data Stewardship Part2 - Prediction of Airbnb Rental Prices using Machine Learning

-- Part2: --
In the GitHub repository (https://github.com/kempefelix/Prediction-of-Airbnb-Rental-Prices-using-Machine-Learning), only the files directly relevant to the modeling are included for storage reasons; the full datasets are not checked in. The original CSV AB_US_2023.csv (raw_data), the cleaned version AB_US_2023_DATA_CLEANED.csv (data/mid_processing), and the preprocessed file AB_US_2023_PROCESSED.csv (data/processed_data) are omitted due to their large size. They can instead be downloaded via the following link and placed into the corresponding directories:
https://tuwienacat-my.sharepoint.com/:f:/g/personal/e12327971_student_tuwien_ac_at/Ei4OQwdYYXJBvkgyrpgQOkMBmbvwrhTqC6YCQP6Q8UtzQQ?e=7Hd7tC

For the actual modeling, predefined subsamples in data/sampled_data—already stratified, split, and uploaded to DBRepo (since DBRepo(https://test.dbrepo.tuwien.ac.at/database/20007276-c04a-4c21-b12f-5aed3fe39388/info) does not support dataset splits natively)—are used to reduce data volume.

The machine-learning pipeline in Modeling_Regression.ipynb employs a RandomForestRegressor with three hyperparameters and conducts a 10-fold cross-validation tuning exclusively on the training data. Because cross-validation automatically handles the train/validation split, the raw data are not manually subdivided into training, validation, and test sets; only a training set and a separate test set exist.

For Part 2 of the exercise, only Modeling_Regression.ipynb is relevant: it loads the training and test data via the DBRepo API, runs the training, and saves all outputs—the trained model, the residual and histogram plots, the true-vs-predicted plots, and a CSV of the final metrics—in the results/ folder at the project root. All other notebooks in the repository are provided for context; to run them you must first download the large data files and adjust the marked file paths in their cells.
--






-- RUN NOTEBOOKS --
There are two distinct ways of reproducing the Results outlined in the report.

The "Modeling_Regression" Notebook can be directly executed using Template data, or the entire exploration and 
preprocessing workflow can be applied before executing the Regression Analysis

Type 1: Standalone Regression Analysis
    Simply execute the Notebook "Modeling_Regression" as-is.

Type 2: Replicate entire Workflow
1. download ZCTA data from the "here -> https://tuwienacat-my.sharepoint.com/:u:/g/personal/e12327501_student_tuwien_ac_at/EdmpPAIWJdlBhMZFuD4YQUkBdLmbF7EOSdesEdLkq7z3bA?e=5iD0J0"
and drop into the folder "data/zcta"
2. Execute "Data_Exploration.ipynb" (optional)
3. Execute "Pre_processing.ipynb"
4. Execute "ZIP-Code encoding.ipynb"
5. Change filepath in "Modeling_Regression.ipynb" to "data/processed_data/AB_US_2023_PROCESSED"
6. Execute "Modeling_Regression.ipynbws "
--