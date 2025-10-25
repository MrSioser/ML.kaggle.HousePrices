# 🏠 House Prices Prediction (Kaggle)

This project predicts housing prices using machine learning models trained on the [House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques) dataset.

---

## Project Structure

```
ML.KAGGLE.HOUSEPRICES/
│
├── data/                    # Original Kaggle dataset (not included, see below)
├── processed_data/           # Cleaned and feature-engineered data (ignored by git)
├── models/                   # Saved trained models (.pkl)
├── submissions/              # Kaggle submission files (.csv)
├── notebooks/                # Jupyter notebooks
│   └── model.ipynb           # Final training script
├── requirements.txt          # Python dependencies
├── .gitignore                # Ignore rules for data, models, and temp files
└── README.md                 # Project overview (this file)
```

---

## Project Goal

To develop a regression model that accurately predicts **SalePrice** based on various house attributes (e.g., area, condition, location, and overall quality).

---

## 🚀 How to Run This Project

Follow these steps to reproduce the workflow and results:

### 1️⃣ Clone the repository
```bash
git clone https://github.com/MrSioser/ML.kaggle.HousePrices.git
cd ML.kaggle.HousePrices
```

### 2️⃣ Download the dataset from Kaggle
Go to the Kaggle competition page:  
👉 [House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)

Download the following files and place them into the `/data` directory:
- `train.csv`
- `test.csv`
- `sample_submission.csv`

Your structure should look like:
```
data/
├── train.csv
├── test.csv
└── Data_Description.txt
```

### 3️⃣ Create a virtual environment (recommended)
```bash
python -m venv venv
source venv/bin/activate        # For Mac/Linux
venv\Scripts\activate         # For Windows
```

### 4️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

### 5️⃣ Run the Jupyter notebook
```bash
jupyter notebook notebooks/model.ipynb
```

### 6️⃣ View results
- The trained model will be saved in `/models/trained_model.pkl`
- Predictions will appear in `/submissions/submission.csv`
- RMSLE metric ≈ 0.105 (~11% relative error)

---

## Workflow

1. **Data Loading & Cleaning**
   - Remove irrelevant columns (`Id`)
   - Handle missing values with imputation strategies
   - Detect and remove outliers (e.g., `GrLivArea`)

2. **Feature Engineering**
   - Create new features such as:
     - `TotalSF` = `1stFlrSF + 2ndFlrSF + TotalBsmtSF`
     - `Age` = `YrSold - YearBuilt`
   - Encode categorical features with `OneHotEncoder`
   - Scale numerical features with `StandardScaler`

3. **Model Training**
   - Primary model: **XGBRegressor**
   - Hyperparameters tuned for optimal RMSLE performance

4. **Evaluation**
   - Metric: **RMSLE (Root Mean Squared Logarithmic Error)**
   - RMSLE = 0.105 → ≈ 11% average multiplicative error

5. **Model Saving & Submission**
   - Save model to `/models/trained_model.pkl`
   - Apply preprocessing pipeline to test data
   - Generate predictions → export to `/submissions/submission.csv`

---

## Data Source & Required Files

Download the following files from the Kaggle competition:
[House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)

**Required files:**
- `train.csv`
- `test.csv`

Place them inside the `data/` and `submissions` folders before running the notebook or script.

## Results Summary

|   Metric  | Score | Interpretation |
|-----------|-------|----------------|
| **RMSLE** | 0.105 | ≈ 11% average multiplicative error |

This result provides a strong baseline for the Kaggle competition.