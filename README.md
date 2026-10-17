# Industrial Impacts on Surface Water Quality (WQI Regression)

Paper: https://ieeexplore.ieee.org/document/11491166/

Reproduces the methodology of the ICCIT 2025 paper "Assessment of Industrial
Impacts on Surface Water Quality in Dhaka and Sylhet Rivers, Bangladesh: Using
WQI and Machine Learning Models".

## Datasets

Two files in the same folder:
- `dhaka_rivers.csv` (Buriganga, Shitalakkhya)
- `sylhet_rivers.csv` (Surma, Kushiyara, Manu, Khowai)

Columns needed: pH, DO, BOD, COD, TDS, SS, EC, WQI.

## What each cell does

1. Preprocessing (run for both regions): median fill then KNN(k=5) imputation,
   duplicate removal, MinMax scaling then z-score standardization, 80/20
   train/test split.
2. Training: Random Forest, Bagging, Gradient Boosting, XGBoost regressors.
   Reports R2, RMSE, MAE, MAPE per region and saves `{region}_model_results.csv`.
3. Analysis per region with the best model: actual-vs-predicted plot
   (`{region}_actual_vs_predicted.png`) and correlation heatmap
   (`{region}_correlation.png`).

## Requirements

pandas, numpy, scikit-learn, xgboost, matplotlib, seaborn.

## Expected outcome

Gradient Boosting should lead both regions, matching the paper
(Sylhet R2 ~0.9917, Dhaka R2 ~0.9871).
