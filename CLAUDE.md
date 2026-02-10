# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Machine Learning capstone project for customer segmentation and acquisition prediction. It analyzes German demographics data to identify potential customers for a mail-order company using unsupervised and supervised learning techniques.

**Primary artifact:** `Arvato_Project_Workbook.ipynb` - A single Jupyter notebook containing the entire ML pipeline.

## Running the Project

```bash
# Install dependencies
pip install numpy pandas scikit-learn xgboost matplotlib seaborn progressbar

# Launch the notebook
jupyter notebook Arvato_Project_Workbook.ipynb
```

**Data requirement:** CSV files must be placed in a `/data/` subdirectory. Data is not included in the repository due to Arvato's terms and conditions.

## Architecture

The notebook follows a four-part ML workflow:

1. **Part 0 - Data Exploration:** Load and profile 4 datasets (891K general population, 191K customers, 42K training/test campaign targets)

2. **Part 1 - Customer Segmentation (Unsupervised):**
   - Data preprocessing: handle missing values (>40% threshold), convert missing codes to NaN
   - Feature engineering: one-hot encoding, mixed-type feature handling (PRAEGENDE_JUGENDJAHRE, CAMEO_INTL_2015, LP_LEBENSPHASE variants, WOHNLAGE, PLZ8_BAUMAX)
   - PCA dimensionality reduction (200 components, 95% variance)
   - KMeans clustering (6 clusters via elbow method)

3. **Part 2 - Supervised Learning:**
   - Models evaluated: Gradient Boosting (best), Random Forest, XGBoost, Logistic Regression
   - GridSearchCV for hyperparameter tuning
   - ROC-AUC as primary metric (achieved 0.79068 on test)

4. **Part 3 - Kaggle Competition:** Generate `submission.csv` with predictions

## Key Dependencies

```python
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler, OneHotEncoder, LabelEncoder
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.model_selection import GridSearchCV
from sklearn.metrics import roc_auc_score, roc_curve, confusion_matrix
import xgboost as xgb
```

## Input Data Files

| File | Description | Shape |
|------|-------------|-------|
| Udacity_AZDIAS_052018.csv | General population demographics | 891,211 × 366 |
| Udacity_CUSTOMERS_052018.csv | Customer demographics | 191,652 × 369 |
| Udacity_MAILOUT_052018_TRAIN.csv | Labeled campaign targets | 42,982 × 367 |
| Udacity_MAILOUT_052018_TEST.csv | Unlabeled test set | 42,833 × 366 |
| DIAS Attributes - Values 2017.xlsx | Feature value descriptions | - |
| DIAS Information Levels - Attributes 2017.xlsx | Feature metadata | - |

## Computational Notes

- Working with 891K+ rows requires substantial RAM during PCA and clustering
- Notebook cells should be run sequentially from Part 0 through Part 3
- Feature preprocessing functions are defined once and reused across datasets
