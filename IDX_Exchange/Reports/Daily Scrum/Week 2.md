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
1. Created Notebook for week 2
2. Set up jupyter notebook for vscode
	- Had some trouble setting up the environment, but using a virtual machine i was able to download the required imports
3. Downloaded Datasets 202505-202605
4. 