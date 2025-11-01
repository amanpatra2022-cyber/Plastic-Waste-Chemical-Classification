# Spectral SVM Classification

Train and evaluate an SVM on spectral data (PCA + StandardScaler + RBF SVM). The repository contains a script that trains on a provided Excel dataset and evaluates on two test sets (low and high noise), producing confusion matrices, PCA explained variance and precision–recall curves.

## Repository structure

- `src/train_eval_svm.py` — main script to train and evaluate the model
- `requirements.txt` — Python dependencies
- `notebooks/` — optional exploratory notebooks

## Data format

The script expects an Excel file with these sheets:
- `trainSet` — training set (rows = samples)
- `testSetLowNoise` — low-noise test set
- `testSetHighNoise` — high-noise test set

Each sheet must contain:
- A `class_id` column with integer class labels (1..5 expected in the script)
- Spectral numeric columns (feature columns). Columns with names matching metadata patterns like `class`, `id`, `row`, `col`, `sample`, `index` are automatically detected as metadata and ignored as spectral features.

If your Excel file is elsewhere, update the `EXCEL_PATH` constant in `src/train_eval_svm.py`.

## How to run

1. Create a Python virtual environment and install dependencies:
```bash
python -m venv venv
source venv/bin/activate    # or `venv\Scripts\activate` on Windows
pip install -r requirements.txt
