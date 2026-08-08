Education Enrollment Prediction - ML & ANN

Predicting whether an education-platform lead will convert into a paying customer. This project applies exploratory data analysis, 
feature engineering, and multiple classification models to help X Education prioritize high-intent leads.
The selected model, CatBoost, achieved 94.36% validation accuracy and 92.06% recall on converted leads.

Business problem:
X Education generates leads through its website, search engines, referrals, and other channels. Although the business 
historically converts roughly 30% of leads, the sales team needs a reliable way to identify the leads most likely to become customers.

The objective is to predict the binary `Converted` target and use the model output as a lead score. A higher score indicates a hotter, 
higher-priority lead for the sales team.

Project workflow:

1. Load and inspect the training and test data.
2. Perform exploratory analysis of lead sources, activity, occupation, and conversion behaviour.
3. Clean the data by removing identifiers, constant columns, low-variance features, and unsuitable rare categories.
4. Standardize category labels, group infrequent categories as `Other`, encode categorical variables, and scale features where required.
5. Train and compare machine-learning and neural-network classifiers.
6. Select the best validation model and create `submission.csv` for the test set.

Dataset:

| File | Description |
| --- | --- |
| `train.csv` | Training data with the `Converted` target. |
| `test.csv` | Test data without the target. |
| `submission.csv` | Final predictions in the required `Id, Converted` format. |

- Training records: 6,468
- Test records: 2,772
- Target: `Converted` (`1` = converted, `0` = not converted)
- Validation split: 80/20 (`random_state=42`)
- Final feature set: 116 engineered features after preprocessing


Data preparation:

Key preprocessing steps include:

- Removed non-predictive identifiers: `Prospect ID` and `Lead Number`
- Removed constant and low-variance features
- Dropped highly sparse or non-informative fields such as `Do Not Call` and `Through Recommendations`
- Standardized equivalent categories, for example `Google` to `google`
- Grouped rare values into `Other` for features such as lead source, last activity, country, tags, and city
- Applied binary encoding, ordinal encoding, and one-hot encoding as appropriate
- Used `StandardScaler` for models sensitive to feature scale

Models evaluated:

The project compares the following classifiers:

- Logistic Regression (GridSearchCV tuned)
- K-Nearest Neighbors (KNN)
- Decision Tree
- Random Forest
- Gradient Boosting
- XGBoost
- AdaBoost
- CatBoost
- Artificial Neural Network (ANN)

Validation results:

Models were evaluated on the held-out validation set. Recall is particularly important because the project objective prioritizes 
capturing leads that are likely to convert.

| Model | Accuracy | Recall |
| --- | ---: | ---: |
| **CatBoost** | **94.36%** | **92.06%** |
| XGBoost | 94.20% | 91.87% |
| Gradient Boosting | 93.74% | 89.48% |
| Logistic Regression | 93.66% | 90.08% |
| ANN | 92.66% | 87.70% |
| AdaBoost | 91.65% | 84.33% |
| Random Forest | 88.64% | 82.74% |
| Decision Tree | 87.56% | 70.83% |
| KNN | 86.71% | 76.98% |

Best model:

**CatBoost** was selected based on the project’s validation comparison. It produced the strongest combination of accuracy and recall, 
correctly identifying **92.06%** of converted leads in the validation set.

The notebook trains the selected model on the prepared training data and generates predictions for every record in `test.csv`.

Repository structure:

```
.
├── Education_Enrollment_ML_and_ANN-3.ipynb  # Analysis, training, evaluation, and prediction
├── train.csv                                # Training data (add locally)
├── test.csv                                 # Test data (add locally)
├── submission.csv                           # Generated test predictions
└── README.md
```

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

### 2. Create and activate a virtual environment (recommended)

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost catboost tensorflow jupyter
```

### 4. Add the data

Place `train.csv` and `test.csv` in the same directory as the notebook.

### 5. Run the notebook

```bash
jupyter notebook Education_Enrollment_ML_and_ANN-3.ipynb
```

Run the cells from top to bottom. The final cell writes `submission.csv` with these columns:

```csv
Id,Converted
8305,0
1591,1
```

## Technologies used

- Python
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- XGBoost
- CatBoost
- TensorFlow / Keras
- Jupyter Notebook

## Notes

- The project brief describes lead scores as values from 0 to 100. The current submission file contains binary predictions (`0` or `1`) in
- the required format used by the notebook.
- For a probability-based lead score, use `predict_proba(... )[:, 1] * 100` for compatible models, rather than the thresholded class
- prediction.

## Author

Shiji Govindan
