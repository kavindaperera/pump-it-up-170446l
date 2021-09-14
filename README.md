# Pump it Up: Data Mining the Water Table
##### _HOSTED BY DRIVENDATA_

### username `moracse_170446l`

## EDA
- Since the data set contains `38` features, `pandas_profiling`  was used to explore the data set. 
- The `eda_output.html` file contains the generated Profile Report. This report contains a complete analysis of data including distribution plots, correlation heatmaps, pairplots etc.  
- An imbalance in the data was identified. The classes (labels) don't have an even distribution. Therefore  `F1 score` and `ROC AUC` was selected as the most suitable metric to evaluate. 

| functional | non functional | functional needs repair |
| :---: | :---: |  :---:|
|32259|22824|4317|

- Features with `missing` values and `zero` values were identified.
- Categorical features with `high cardinality` were identified. 
- Features with `high correlation `were identified.

## Preprocessing and Feature Engineering

#### Handling Missing Values, Zero Values and Outliers
1. Both `missing` values and `zero` values of `permit`, `funder` and `installer` were filled.
2. `scheme_name` was dropped because it has `28166` (higher than others) missing values.
3. `zero` values (outliers) of  `longitude` were filled with median value.

#### Creating New Features

- Two new features `year_recorded` and `month_recorded` were created using `date_recorded`. `date_recorded` was dropped. 

#### Label Encoding

- Label encoding was used on categorical variables and class labels.

## Feature Selection

#### High Cardinality
- `wpt_name` and `subvillage` were dropped due of high cardinality.

#### High Correlation
- Some highly correlated features were identified and some were droped.

## Model Selection

- `XGBoost` was selected after comparing baseline models of `XGBoost` and `Randomforest`. 

#### Hyperparameter Optimizarion
- `RandomeSearchCV` was used for hyperparamter tuning. 
- Parameters with best scores were used on the final model.
- Different metrics [ `F1 score`, `ROC AUC`] were used to check the perfomance.

#### Feature Importance
- Feature importance was used to compare the relative importance of the selected features. Some features with low scores were removed to improve the model.
- Dimensionality reduction was not a huge concern, since the dataset is of reasonable size. 

## Submissions

| BEST | CURRENT RANK | # COMPETITORS | Date |
| ------ | ------ | ------ | ------ |
| 0.8102 | 2259 | 12381| Sept. 14, 2021 |

![best submission](https://github.com/kavindaperera/pump-it-up-170446l/blob/main/submission_proof.PNG?raw=true)

![all submissions](https://github.com/kavindaperera/pump-it-up-170446l/blob/main/submissions.PNG?raw=true)


