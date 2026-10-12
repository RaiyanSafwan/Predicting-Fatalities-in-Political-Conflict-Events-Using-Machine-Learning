# Predicting Fatalities in Political Conflict Events Using Machine Learning

A machine-learning project that predicts whether a political conflict event will involve fatalities, using event-level features from the **Conflict data set (2019-2026)**.

## Project overview

The notebook explores the dataset, creates a binary target from the `fatalities` column, preprocesses selected event features, trains multiple classifiers, and compares their evaluation metrics.

### Target variable

The notebook creates `fatal_event` as follows:

- `0`: no fatalities (`fatalities == 0`)
- `1`: fatalities occurred (`fatalities > 0`)

### Features used

The current notebook selects these input features:

- `event_type`
- `sub_event_type`
- `country`
- `interaction`
- `region`
- `year`
- `population_5km`

It one-hot encodes categorical features, fills missing feature values with `0`, and uses an 80/20 train-test split with `random_state=42`.

### Models implemented

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- AdaBoost
- XGBoost
- CatBoost

The notebook compares model performance using accuracy, precision, recall, F1-score, and ROC-AUC. It also creates visual evaluations such as an accuracy comparison and CatBoost confusion matrix / ROC curve.

> **Important:** Results depend on the dataset version and the notebook environment. Run the notebook to generate the current metrics; no performance score is claimed in this README.

## Repository contents

Expected project structure:

```text
Predicting-Fatalities-in-Political-Conflict-Events-Using-Machine-Learning/
├── Predicting Fatalities in Political Conflict Events.ipynb
├── Conflict data set (2019-2026).csv
├── README.md
├── requirements.txt
├── .gitignore
└── outputs/                         # optional generated plots/results
```

The CSV is a local input file and must be placed in the project root with the exact filename shown above, unless you update the notebook's `pd.read_csv(...)` path.

## Requirements

- Python 3.10 or newer recommended
- Jupyter Notebook or JupyterLab
- The Python packages listed in `requirements.txt`

## Setup and run

1. Clone this repository or download its files.
2. Place `Conflict data set (2019-2026).csv` in the same folder as the notebook.
3. Create and activate a virtual environment (recommended).
4. Install dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

5. Start Jupyter:

   ```bash
   jupyter notebook
   ```

6. Open `Predicting Fatalities in Political Conflict Events.ipynb` and run the cells from top to bottom.

### Windows PowerShell environment example

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter notebook
```

If PowerShell blocks environment activation, you can still install packages using the Python environment you intend to use, or use Command Prompt activation instead.

## Dataset

The notebook expects a CSV named:

`Conflict data set (2019-2026).csv`

This README does not establish the dataset's original publisher, collection methodology, or redistribution license. Preserve the dataset's original attribution and license information, and confirm you have permission to publish it before committing the CSV to a public repository.

**GitHub file-size note:** GitHub blocks regular Git files larger than 100 MB. Check the CSV size before pushing. If it is larger than 100 MB, do not try to push it as a normal file; use Git LFS or publish documented download instructions instead. Do not upload private, restricted, or sensitive data.

## Methodology at a glance

1. Load the CSV with pandas.
2. Explore dataset shape, columns, missing values, and descriptive statistics.
3. Create the binary `fatal_event` target from `fatalities`.
4. Drop available columns among `event_date`, `notes`, `source`, and `timestamp`.
5. Select the seven features listed above.
6. One-hot encode categorical variables and fill remaining feature missing values with `0`.
7. Split the data into training and testing sets (80/20, random state 42).
8. Train and compare the seven classifiers.
9. Review classification metrics, ROC-AUC, and plots.

## Limitations and responsible use

- A high accuracy alone may hide poor performance on the less frequent class; inspect precision, recall, F1-score, confusion matrices, and class balance.
- The current notebook uses a random train-test split. It does not by itself establish that predictions generalize to future years or unseen regions.
- Predictions are statistical estimates, not certainty about real-world events. Do not use them as the sole basis for operational, political, or safety-critical decisions.
- Review potential data leakage, class imbalance, missing-data handling, and model calibration before making stronger claims.

## Team

Add or update the project contributors here:

- Raiyan Safwan
- Add other team members as appropriate

## License

No license is specified here. Add a license only after confirming that the project code and dataset may be distributed under its terms.
