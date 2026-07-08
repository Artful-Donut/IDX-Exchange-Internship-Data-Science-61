# Wednesday Meeting
Questions:
- Do we have to be collaborators on github?
- Mismatched Datasets:
	- Stack them together
	- Not filled columns are not bad, don't need to worry about them (they will also get filtered out)
- 

|              |                                                                                                                              | TO-DO                                        |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| Cici Xiu     | Exploring datasets<br>Came across mismatched columns<br>Looked at mean distributions<br>Drew some plots to show distribution | Explore inter-variable relationships         |
| Amy Trinh    | Putting datasets together, needed to scale by log to see distributions<br>Filtered ahead of time<br>Looked at metadata       | Bi-variate analysis to see changes in months |
| Wenxin Cui   | Loaded one year of data (may 2025-2026<br><br>Made diagrams of distribution<br>Distributions of lot sizes                    | Load more next week                          |
| Anh Tran     | Loaded dataset<br>Combined to one<br><br>Looked up statistics and missing values of each column (check column consistency)   | Get more of the EDA finished                 |
| Lynne Nguyen | Dataset                                                                                                                      | Catch up LOL                                 |
| Yujian Tan   | Downloaded data, showed mismatched (filled and not filled have different columns)                                            | Catch up LOL :D                              |

- 
# Report
## Todo:
- Data Exploration
	1. Load minimum 6 months of dataset into pandas
	2. Explore Distributions of:
		1. ClosePrice (target variable)
		2. LivingArea 
		3. Bedrooms
		4. Bathrooms
		5. LotSize
	3. Restrict Analysis to PropertyType = Residential and SingleFamilyResidence (per task doc)
	4. Deliverable:
		1. Jupyter notebook 01_exploration.ipynb with basic EDA plots
			- (For info on EDA plots, see https://www.geeksforgeeks.org/data-analysis/exploratory-data-analysis-in-python/)

## Progress
1. Setup:
	1. Created Notebook for week 2
	2. Set up jupyter notebook for vscode
		- Had some trouble setting up the environment, but using a virtual machine i was able to download the required imports
	3. Downloaded Datasets 202505-202605
	4. Combined them 
		- No issues with missing datapoints thus far, just some mismatched data
2. Isolated each relevant column and used `dataframe.describe()`
	- Around 130k datapoints 
	- All datasets have outliers that mess with visualization. Seems alright though. :P
3. Visualized datasets with histograms, box plots, and bar charts
4. Decided when to normalize datasets
	- House prices needed to go by a log scale
	- Pretty much every datapoint had outliers that messed with visualization 
		- Continuous values like closing price, living area, and lot size would probably benefit the most from normalization though. The outliers make all of the histograms look the same
		- Number rooms (bed/bath) are fine though. They're discrete and the distribution is still legible (minus the box plots lol, I have versions with outliers and one without but I'm not sure this is the best way to go about it)
5. Transformed continuous data with log (outliers are important, but they mess with visualization)
	- found this one pretty helpful: https://www.geeksforgeeks.org/data-science/log-transformation/ 
6. Continuous data was visualized using box plots and histograms. Discrete data was visualized with box plots and bar graphs.
	- Results:
		1. Close Price: Had the largest range and the most outliers, though once log transformed and scaled, data seems to be skewed to the right.
		2. Living Area: Distribution was similar to Close Price once log transformed and skaled, though the range was smaller.
		3. Bedrooms: Lots of outliers, though most seemed to fall in between 3-4
		4. Bathrooms: Similar to bedrooms, though most fell in between 2-3
		5. Housing Size: Had a nonuniform distribution according to the histogram, though frequency seems to be concentrated in the middle and ends.
7. Bivariate data analysis was performed
	- Results:
		1. There seems to be interesting behaviour when any of the values are zero, needs discussion. Could possibly be an error.
		2. For variables (excluding lot size square feet), most vaguely resemble a messy logarithmic relationship
		3. Lot size square feet seems to have a linear relationship, though the close price stays within a certain range irrespective of Close Price

## Research
1. Data with outliers
	- While a billion dollar sale will undoubtedly skew results and make readability harder,
	- Luckily, I think this article approaches the topic pretty well (and serves as a reminder for me to research parametric + nonparametric methods of)
		- https://statisticsbyjim.com/basics/remove-outliers/
2. Transforming data (also mentioned in the previous article)
	- "In regression analysis, you can try transforming your data or using a robust regression analysis available in some statistical packages." <- Applies to statistical analysis specifically, but the idea is still there
3. 