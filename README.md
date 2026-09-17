# Network Intrusion Detection

Binary classification of network connections using a dense neural network and a logistic-regression baseline on NSL-KDD.

## What this project demonstrates

- Mixed numerical and categorical feature preprocessing
- Neural classification with early stopping
- Evaluation against a classical baseline using F1, ROC-AUC and a confusion matrix
- Export of both the model and its fitted preprocessing pipeline

## Evaluation design

The corrected notebook preserves the official train/test separation. Validation comes only from the training file; scalers and encoders fit only the training subset. The difficulty annotation is excluded from model inputs.

## Setup

Use Python 3.10 or 3.11. From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab
```

Open the notebook under `notebooks/` and run its cells in order. Data belongs in `data/`; generated results go to `artifacts/`.

See [input schema](data/README.md).

## Results and provenance

Corrected benchmark results are pending a full run with the external dataset. Historical 99.27% accuracy came from a different, flawed protocol that combined the official train and test files and fitted preprocessing before splitting. It is not a score for the corrected notebook.

The original notebook and weights remain under `legacy/` for provenance. Those weights lack a saved preprocessing mapping and should not be used with the new pipeline. The original author code remains available in Git history.

## Files

| Path | Purpose |
|---|---|
| `notebooks/intrusion_detection.ipynb` | Corrected training and evaluation |
| `data/` | Input instructions |
| `artifacts/` | Generated models, metrics and learning curve |
| `legacy/` | Original experiment, not current benchmark evidence |

## Limitations

NSL-KDD is a historical benchmark; performance on it does not establish performance on modern live network traffic. 
