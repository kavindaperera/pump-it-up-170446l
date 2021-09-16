# Pump it Up: Data Mining the Water Table 
##### _HOSTED BY DRIVENDATA_ 
[competition link](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/)

### username `moracse_170446l`

## EDA
- First, `pandas_profiling`  was used to explore the data set. The [eda_output.html](./eda_output.html) file contains the generated Profiling Report. This report contains a complete analysis of data including distribution plots, correlation heatmaps, pairplots etc.  
- An imbalance in the dataset was identified. The class labels (multiclass) don't have an even distribution. (Therefore  `Weighted F1-score` and `Weighted AUC` was selected as the most suitable metrics to evaluate.)

| functional | non functional | functional needs repair |
| :---: | :---: |  :---:|
|32259|22824|4317|
- Features with `missing` values and `zero` values were identified.
- Categorical features with `high cardinality` were identified. 
- Features with `high correlation `were identified.
- Distributions and Outliers of data were analysed using histograms.

## Preprocessing and Feature Engineering

#### Handling Missing Values, Zero Values and Outliers
1. `missing` values of `permit`, `public meeting`, `funder` and `installer` were handled.
2. `zero` values (outliers) of  `longitude` and `gps_height` were filled with mean value grouped by `region_code`. `0` values are not possible in Tanzania.
3. `zero` values (outliers) of  `construction_year` were filled with median values by grouping.
4. `scheme_name` was dropped because it has `28166` (training set) missing values.
5. `amount_tsh` , `num_private` and `population` were dropped because they contain too many `zero` values.
6. Some spelling mistakes in `installer` were identified and handled.

#### Creating New Features

- Two new features `year_recorded` and `month_recorded` were created using `date_recorded`. `date_recorded` was dropped. 

#### Encoding

- Label encoding was used on categorical variables.
- Label encoding was used on class labels.

## Feature Selection

#### High Cardinality
- `wpt_name` and `subvillage` were dropped due of high cardinality.
  * `wpt_name`: 37400 distinct values.
  * `subvillage`: 19287 distinct values

#### High Correlation
- Some highly correlated features were identified and some were droped.
  *  `extraction_type_group`, `extraction_type` and `extraction_type_class`
  *  `management_group` and `management`
  *  `payment` and `payment_type`
  *  `water_quality` and `quality_group`
  *  `quantity` and `quantity_group`
  *  `source_type`, `source` and `source_class`
  *  `waterpoint_type` and `waterpoint_type_group`

## Model Selection

- `XGBoost` was selected after comparing baseline models of `XGBoost` and `Randomforest`. 

#### Hyperparameter Optimization
- `RandomeSearchCV` was used for hyperparamter tuning. 
- Parameters with best scores were used on the final model.
- Different metrics [ `Weighted F1 score`, `Weighted ROC AUC`] were used to check the perfomance.

#### Feature Importance
- Feature importance was used to compare the relative importance of the selected features. Some features with low scores were removed to improve the model.
- Dimensionality reduction was not a huge concern, since the dataset is of reasonable size. 

## Submissions

| BEST | CURRENT RANK | # COMPETITORS | DATE |
| :------: | :------: | :------: | :------: |
| 0.8162 | 1718 | 12416 |  Sept. 15, 2021 UTC. |

![best submission](https://github.com/kavindaperera/pump-it-up-170446l/blob/main/submission_proof.PNG?raw=true)

![all submissions](https://github.com/kavindaperera/pump-it-up-170446l/blob/main/submissions.PNG?raw=true)


## For More Information

See the full EDA in [eda_output.html](./eda_output.html).

See the full training process in the [Jupyter Notebook](./pump-it-up-notebook-xgboost.ipynb).


