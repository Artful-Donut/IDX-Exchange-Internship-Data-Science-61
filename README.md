# IDX-Exchange-Internship-Data-Science-61
Results of the IDX Exchange Data Science Internship, creating a model to predict residential close prices in San Francisco. 
(Note: Due to security concerns, raw data and internship details are not included in the repository.)

## Results
The best results were achieved with sci-kit's Histogram Gradient Boost model, with these statistics:

| R2 | Median Absolute Error | Mean Absolute Percentage Error |
| --- | --- | --- |
| 0.9200822439269665 | 60420.22765593766 | 0.8252734425585966 |

## How to use this Repository
The workload is divided into six different files for different sections of work. The most relevant files for viewing can be found as follows:

```
IDX_Exchange/deliverables
├── 01_exploration.ipynb
├── 02_preprocessing.ipynb
├── 03_baseline_model.ipynb
├── 04_model_comparison.ipynb
├── 05_advanced_models.ipynb
├── 06_evaluation.ipynb
├── CRMLS_202505_202604_training_set.csv
├── CRMLS_202505_202604_training_set_fe.csv
├── CRMLS_202605_testing_set.csv
├── CRMLS_202605_testing_set_fe.csv
├── evaluations.csv
└── histgrad_perfermance_per_priceband.csv
```

**Jupyter Notebooks 01-06**:
1) Basic EDA plots of raw data (filtered for single family residential listings) before preprocessing
2) Preprocessing and exporting data as a new csv
3) Basic Linear Regression of Data
4) Comparison of Decision Tree and Random Forest models
5) Comparison of Histogram Gradient Boosted model and XGBoost
6) Evaluation of every model (+ Hyperparameter Tuning) with R2, MdAE, and MAPE metrics, as well as further analysis

**CSV Files:**
1) CRMLS_202505_202604_training_set: Training set from May 2025 - May 2026
2) CRMLS_202505_202604_training_set_fe: Training set from May 2025 - May 2026 + Feature Engineered columns
3) CRMLS_202605_testing_set: Testing set with data from June 2026
4) CRMLS_202605_testing_set_fe: Testing set with data from June 2026 + Feature Engineered columns
5) evaluations: Evaluation of each model per metric
6) histgrad_perfermance_per_priceband: Histogram Gradient Boosted performance per price band

# Dataset 
## Sourcing
Dataset was sourced from IDX Exchange's servers, consisting of an aggregate of multiple listings on various MLS platforms.

## Initial Evaluation
<img width="710" height="454" alt="Histogram of Close Prices from May 2025 - May 2026" src="https://github.com/user-attachments/assets/32bc9251-3441-4c0f-8be8-4b9ec3be28b4" />
<img width="690" height="454" alt="BoxPlot of Close Prices from May 2025 - May 2026" src="https://github.com/user-attachments/assets/ce66278d-53da-41c0-9e9e-c68f1103d571" />

Initial evaluation of the data showed that the even when filtering for Residential and Single-Family properties, the range caused issues with data showing (and pretty much all graphs needed to be log-transformed)

## Preprocessing
Preprocessing the data occurred in multiple steps (see 02_preprocessing.ipynb):
1) Removing columns
   - Columns that weren't necessary (such as information related to the buyer, days on market, and other personal details) were removed
   - Sale date was removed post-preprocessing, as date was a hyperparameter for data analysis
2) Refine search
   - Only use sales for Residential Single-Family properties (as that was scope chosen for this project)
   - Ended up shortening the dataset the most with a 30% reduction
3) Further remove columns that mostly consisted of N/A values
4) Drop bad data points
   - This includes duplicate data points or values with missing Close Price
7) Split data set into training (May 2025 - May 2026) and testing (June 2026)
   - Splitting data chronologically rather than randomly allows us to test recent data more easily
8) Removing outliers (from the lower and upper 1% of sales)
   - This includes duplicate data points or values with missing Close Price
   - Ensured models fitted properly without arbitrarily taking out too many values
9) Imputing missing values
   - For columns with no proper default values (like geographical data), values were inferred from other columns (such as longitude / latitude)
10) Encoding categorical values
11) Feature Engineering
   - Engineered certain fields from current fields (such as bedroom / living space ratio)
   - Using a California district dataset, added fields such as homeless population.
   - Due to time and life constraints, Feature Engineered datasets were not used in the final evaluation. 
