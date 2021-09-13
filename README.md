# Pump it Up: Data Mining the Water Table
##### _HOSTED BY DRIVENDATA_

## EDA
- Since the data set contains `38` features, `pandas_profiling`  was used for explore the data easily. `output_EDA.html` contains the generarted profile report. This report contains a complete analysis of data including distribution plots, correlation heatmaps, pairplots etc.  
- An imbalance in the data was identified. The classes (labels) don't have an even distribution. Therefore `F1 score` was selected as the most suitable metric to evaluate. 

| functional | non functional | functional needs repair |
| :---: | :---: |  :---:|
|32259|22824|4317|

- Feature with `missing` values and `zero` values were indentified.
- Categorical columns with `high cardinality` were identified. 
- Categorical columns with `high correlation `were identified.

## Preprocessing

#### Missing Values and Zero Values
1. Both `missing` values and `zero` values of `permit`, `funder` and `installer` were filled.
2. `scheme_name` was dropped because it has `28166` (higher than others) missing values.

## Feature selection

#### High cardinality
- `wpt_name` and `subvillage` were dropped due of high cardinality.

#### High correlation
- Some highly correlated features were identified and some were droped. 


## Model Selection

- `XGBoost` was selected after a comparing baseline models of XGBoost and Randomforest. 
- `XGBoost` is known to perform well in imbalance classification. 

#### hyperparameter optimizarion
- `RandomeSearchCV` was used for hyperparamter tuning. 
- Parameters with best scores where used on the final model.

#### Feature Importance
- Feature importance checked and used to improve the model. Some features with low scores were removed.
- Dimentionaly Reduction was not a huge concern, since the dataset is of reasonable size. 

## Submissions

| BEST | CURRENT RANK | # COMPETITORS |
| ------ | ------ | ------ |
| 0.8102 | 2256 | 12377|

![alt text](https://github.com/kavindaperera/pump-it-up-170446l/blob/main/submission_proof.PNG?raw=true)

