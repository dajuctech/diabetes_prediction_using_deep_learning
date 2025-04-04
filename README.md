# Diabetes Prediction Using Deep Learning

This repository implements a deep learning approach for predicting diabetes using a structured pipeline that includes data loading, exploratory analysis, preprocessing, model training, and evaluation. The code leverages TensorFlow/Keras for building the neural network model, along with various libraries for data manipulation and imbalance handling.

---

## 1. Environment Setup

- **Library Installation:**  
  Installs necessary packages such as `ace_tools`, `imblearn`, and `keras-tuner`.
  
- **Imports and Configuration:**  
  Loads core libraries (Pandas, NumPy, Seaborn, Matplotlib) and deep learning frameworks (TensorFlow, Keras). It also imports tools for oversampling (SMOTE, RandomOverSampler), scaling (StandardScaler, MinMaxScaler), and metrics evaluation.
  
- **Reproducibility:**  
  Sets random seeds for Python, NumPy, and TensorFlow to ensure reproducible results.

---

## 2. Data Loading and Exploration

- **Data Import:**  
  Downloads training and test datasets from Google Drive URLs.
  
- **Dataset Overview:**  
  - The training dataset contains 668 entries with 10 features.
  - The test dataset contains 100 entries with 9 features.
  
- **Exploratory Analysis:**  
  - Displays data shapes, summaries, and basic descriptive statistics.
  - Visualizes the distribution of the target variable (`class`), which is imbalanced (437 instances of class 0 vs. 231 of class 1).
  - Checks for missing values, duplicates, and examines feature correlations.

---

## 3. Data Preprocessing

- **Feature Inspection:**  
  - Lists unique values in each column.
  - Identifies features with zeros or outliers using boxplots and statistical summaries.
  
- **Handling Missing or Invalid Values:**  
  Several strategies are implemented, including:
  - Replacing zeros with class-specific mean or median values.
  - Using KNN imputation to fill invalid zeros.
  - Outlier handling through winsorization and IQR capping.
  
- **Feature Extraction:**  
  - Separates the target variable (`class`) and features.
  - Applies label encoding to the target.
  
- **Class Imbalance:**  
  Uses both RandomOverSampler and SMOTE to address imbalanced classes in the training data.

- **Data Splitting and Scaling:**  
  Splits the data into training and validation sets and applies feature scaling (using StandardScaler).

---

## 4. Model Training and Evaluation

- **Neural Network Architecture:**  
  A deep learning model is built using Keras’ Sequential API:
  - The network consists of multiple dense layers with different activation functions (swish and relu), dropout layers for regularization, and L1/L2 regularization on the first layer.
  - The output layer uses a sigmoid activation function for binary classification.
  
- **Compilation and Training:**  
  - Compiled with the binary cross-entropy loss and the RMSprop optimizer.
  - The model is trained for 100 epochs with a batch size of 32, using a validation split to monitor performance.
  
- **Model Evaluation:**  
  - Generates predictions on the validation set.
  - Converts raw predictions into binary class predictions.
  - Evaluates model accuracy and plots training history (accuracy and loss curves) for both training and validation sets.

---

## 5. Test Predictions and Output

- **Test Data Processing:**  
  The test dataset is preprocessed similarly (dropping the `id` column) and scaled using the previously fitted scaler.
  
- **Prediction Generation:**  
  - The trained model predicts diabetes outcomes on the test data.
  - Predictions are converted to categorical values and then decoded back to original labels.
  
- **Result Saving:**  
  Final predictions (raw, categorical, and decoded) are saved to a DataFrame and output to CSV for further use or submission.

---

## Conclusion

This project demonstrates an end-to-end pipeline for diabetes prediction using deep learning. The approach includes thorough data exploration and cleaning, careful handling of imbalanced data, and the development of a custom neural network model with regularization and dropout. The trained model is evaluated with standard metrics, and test predictions are generated and saved for downstream analysis.

