# README.md
// filepath: c:\Users\oasis\projects\github\xgboost-stroke\README.md

# Stroke Prediction with XGBoost

This project analyzes and predicts stroke risk using the Stroke Prediction Dataset from Kaggle. The workflow includes data cleaning, exploratory data analysis (EDA), feature engineering, model training with XGBoost, and fairness evaluation. The project also explores the impact of data leakage and various resampling strategies on model performance and fairness.

## Project Structure

- `healthcare-dataset-stroke-data.csv` — Main dataset for analysis and modeling.
- `xg-boost.ipynb` — Jupyter notebook containing all code for data exploration, preprocessing, modeling, and evaluation.
- `requirements.txt` — List of Python dependencies.
- `rds-res.csv` — Results or processed data (output from the notebook).
- `rds-report.pdf` — Project report.
- `rds-slides.pdf` — Presentation slides.

## Getting Started

### Prerequisites

- Python 3.8+
- Recommended: Use a virtual environment

### Installation

1. Clone this repository.
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```

### Running the Notebook

1. Open `xg-boost.ipynb` in Jupyter Notebook or VS Code.
2. Install dependecies using: pip install -r requirements.txt
3. Run all cells to reproduce the analysis, modeling, and results.

## Main Steps

1. **Data Loading & Exploration:**  
   Load the dataset and perform exploratory data analysis (EDA) to understand distributions and missing values.

2. **Data Cleaning & Preprocessing:**  
   - Handle missing values.
   - Encode categorical variables.
   - Normalize and standardize features.

3. **Resampling:**  
   - Explores and implements SMOTE, SMOTE-Tomek, SMOTE-ENN, and undersampling to address class imbalance.

4. **Model Training:**  
   - Trains an XGBoost classifier and evaluates performance using accuracy, F1, ROC AUC, and confusion matrix.

5. **Evaluation:**  
   - Assess model performance (accuracy, FNR, FPR, etc.).
   - Evaluate fairness metrics using [fairlearn](https://fairlearn.org/). Evaluated metrics (e.g., demographic parity, equalized odds) across sensitive groups (e.g., gender).

6. **Interpretability:**  
   Use SHAP and LIME for model interpretability and feature importance.

## Overall

- Our job was to then tune our XGBoost model to increase the base metrics, while testing two fairness interventions.

- Correlation remover is pre-processing tool to reduce the correlation between non-sensitive features and the sensitive attributes within a dataset. The purpose of this tool is to remove or mitigate bias before the training. 

- ThresholdOptimizer is a post-processing algorithm designed to improve fairness in binary classifcation tasks. It applys group specific thresholds to the predictions of a classifier, optimizing performance while following a fairness constraint. 

- The final results of corrected sampling, tuning and fairness metrics shows that GridSearch with a Threshold Optimizer is our choice for predicting stroke. It achieved the highest precision of 0.939, a recall of 0.744, and tied for the highest F1 score of 0.817.

- In terms of fairness it had the lowest number of false negatives, the lowest demographic parity and the highest demographic parity ratio. 

## Results and Report

- Results and metrics are saved in `rds_res.csv`.
- Visualizations and detailed analysis are available in the notebook.
- Summary and discussion are provided in `rds-report.pdf` and `rds-slides.pdf`.

## References

- [Stroke Prediction Dataset - Kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)
- ADS baseline: [Kaggle Notebook](https://www.kaggle.com/code/tanmay111999/stroke-prediction-effect-of-data-leakage-smote/notebook)

## Authors

- Yash Jha
- Jon Dinh

## License

This project is for educational purposes. Refer to the dataset's license for data
