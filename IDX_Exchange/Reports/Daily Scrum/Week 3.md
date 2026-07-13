# Wednesday Meeting
Questions: 
- The area was a bit confusing for me. How do I use the enum? (For now, I ended up just using the square foot property)
	- 
- Just making sure, recent month = only one month for testing?
- Is 12 months a valid population size? (Currently using May 2025 - May 2026)
- When we're preprocessing the data, we're looking at all values and not just the 5 variables from the previous week correct? (just making sure)
	- There is a few that probably don't affect closeprice though. A lot of values seem to be just medata
- 

|              | Current Progress                                                                                                                                                                                                                                      | TO-DO                                |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| Cici Xiu     | Absent due to scheduling conflict                                                                                                                                                                                                                     |                                      |
| Amy Trinh    | Looked at null values, remove columns (with >80% null values, irrelevant), imputed with mean or 0 when appropriate (may not be the best measure), did train/test split into a separate function so it can be used outside of the function (so smart!) |                                      |
| Wenxin Cui   | Combining data from week 2, dealt with missing data, encoded categorical data with sci-kit<br><br>Imputing missing values: median not mean                                                                                                            |                                      |
| Anh Tran     |                                                                                                                                                                                                                                                       |                                      |
| Lynne Nguyen | Completed EDA                                                                                                                                                                                                                                         | Preprocessing, im so embarrassed LOL |
| Yujian Tan   | Honestly similar to my progress<br><br>Checked missing values, quantified amount of missing outliers<br><br>Concluded scaling and transformation might be necessary for further                                                                       | Catching up to week 3!               |

# Report

## Todo
1. Handle missing values
2. Convert Categorical fields to numeric (encoding)
3. Normalize numerical features
4. Create train/test split
	- Recent month = test set
	- X months immediately preceding = training set
		- X is not fixed and can be a tunable choice 
		- Experiment to find optimal value of X
## Progress
1. Remove unnecessary columns, clean data
2. Split data into training and test :).
3. Handle Missing Values 
	
4. 
## Research
(via AVM_Data_Science_Best_Practices.pdf)
1. Excise Columns
	- ListPrice/OriginalListPrice 
2. Missing Values:
	- Remove observations where ClosePrice <= 0 or just generally missing
		- Do NOT impute
	- Remove Duplicate values (same parcel ID, or address + close date)
	- Remove logical impossibilities (close date earlier than list date), zero or negative square footage, bedroom/bathroom counts inconsistent with living area
	- Some properties may have missing values systematically (eg. lot size is disproportionately missed for condos). Flag these instead.
		- For remove columns with excessive missingness
	- For Lot size, bedroom, bathroom, etc, it might be best to use the median (or maybe make a new feature?)
	- Don't forget to log count and percentage of records removed at each cleaning step. Anything more than 15% drop should be a red flag
3. Features to consider:
	

| Category     | Feature                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Locational   | - Distance to CBD<br>- Major Employment Centers<br>- Top-rated schools (computed with lat/long)<br>- Neighborhood or ZIP-level aggregates (eg. median price per sqft in the last 12 months). Only compute on training data and joined forward to avoid leakage<br>- Geohash/spacial clustring as a categorical feature when neighborhood labels are noisy/incons                                                                                                                                                                                                                                                                                 |
| Temporal     | - Month/season encoded with sine/cosine transforms (capture cyclical seasonality without the jump from december -> january)<br>- Property age at time of sale (not just year built), feature reflects condition-relev                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Categorical  | - High cardinality categoricals (neighborhood, subtype) should use target encoding with cross-validation folds so category's encoding never sees its own rows' label<br>   - Note: Target encoding is imputing the value with the mean of the target value (or maybe median?).<br>      - More on encoding: https://www.geeksforgeeks.org/machine-learning/categorical-data-encoding-techniques-in-machine-learning/ , https://www.geeksforgeeks.org/machine-learning/mean-encoding-machine-learning/<br>	  - with cross-validation: https://medium.com/@prathik.codes/how-to-do-target-encoding-without-data-leakage-the-right-way-280bd24fbc81 |

3. Leakage Prevention (IMPORTANT):
	- All preprocessing (feature engineering, imputation, encoding, scaling, outlier thresholds) must fit on the training data ONLY. And then applied unchanged to test data
	- How to do this structurally:
		1. Wrap imputers, encoders, and scalers in a scikit-learn Pipeline / ColumnTransformer (or equivalent). Fit will only see training data and transform is what affects test data
		2. Fit full pipeline inside each cross-validation during model selection (not just once on the whole training set). Validation folds leak through shared encodings otherwise
		3. Treat groubpy/aggregate feature (neighborhood avg, comps-based features) as a fit-on-train transform. Identical in spirit to an imputer
4. MdAPE
	- Metric for Skewed, Multi-Scale Price Data
	- Report $R^2$, MAPE, MdAPE, and MAE together

|     |     |
| --- | --- |
|     |     |

5. Don't forget to go down the self-check rubric before deciding completion