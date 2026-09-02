# IDX-Exchange-Internship-Data-Science-61
Results of the IDX Exchange Data Science Internship, creating a model to predict residential close prices in San Francisco. 

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
