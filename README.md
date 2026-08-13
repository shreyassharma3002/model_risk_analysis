## Methodology

1. **Data cleaning and preprocessing** — handling missing values, encoding categorical
   variables, and resolving data quality issues (e.g. inconsistent label formatting
   between the Adult Census train/test files).
2. **Exploratory data analysis** — target class balance, correlation heatmaps between
   features and the target variable.
3. **Model training** — XGBoost and Logistic Regression trained on an 80/20 stratified
   train-test split for each dataset.
4. **Class-weighted balancing** — both models retrained with class weighting to address
   recall limitations caused by class imbalance.
5. **Evaluation** — precision, recall, F1-score, and ROC-AUC used instead of raw
   accuracy, given both target variables were imbalanced.

## Key Findings

- **LendingClub (loan default):** both models struggled to predict default risk; no
  individual feature showed a strong correlation with the outcome (max ~0.16).
  Logistic Regression slightly outperformed XGBoost (ROC-AUC 0.68 vs 0.62).
- **Adult Census (income classification):** both models performed strongly, consistent
  with stronger feature correlations (up to 0.33 for education level). XGBoost
  outperformed Logistic Regression here (ROC-AUC 0.93 vs 0.90) — the opposite result
  from the lending dataset.
- **Core insight:** no single algorithm was universally superior across both use cases,
  reinforcing that AI models must be validated independently for each specific
  application rather than assumed fit-for-purpose based on precedent.

## Results Summary

| Dataset | Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|---|
| LendingClub | XGBoost | 0.824 | 0.313 | 0.085 | 0.133 | 0.622 |
| LendingClub | XGBoost (Balanced) | 0.763 | 0.235 | 0.212 | 0.223 | 0.604 |
| LendingClub | Logistic Regression | 0.840 | 0.519 | 0.046 | 0.084 | 0.683 |
| LendingClub | Logistic Regression (Balanced) | 0.640 | 0.239 | 0.570 | 0.337 | 0.684 |
| Adult Census | XGBoost | 0.878 | 0.790 | 0.666 | 0.722 | 0.930 |
| Adult Census | XGBoost (Balanced) | 0.838 | 0.617 | 0.849 | 0.714 | 0.930 |
| Adult Census | Logistic Regression | 0.851 | 0.731 | 0.600 | 0.659 | 0.905 |
| Adult Census | Logistic Regression (Balanced) | 0.808 | 0.568 | 0.831 | 0.674 | 0.905 |

## How to Run

1. Clone the repository:
```bash
   git clone https://github.com/shreyassharma3002/model_risk_analysis.git
   cd model_risk_analysis
```
2. Install dependencies:
```bash
   pip install pandas numpy matplotlib scikit-learn xgboost
```
3. Open `model_risk_analysis.ipynb` in Jupyter Notebook, JupyterLab, or VS Code, and
   run all cells in order.

## Tools Used

- Python (pandas, numpy, matplotlib, scikit-learn, XGBoost)
- VS Code with Jupyter Notebook support
- Git / GitHub for version control

## Author

Shreyas Sreedhara, Master of Data Science, RMIT University

## Acknowledgements

Generative AI (Claude, Anthropic) was used to support code review, debugging, and
drafting during development. See the accompanying report's Generative AI Attribution
statement and Condition 3 Bounded Process AI Declaration for full details.