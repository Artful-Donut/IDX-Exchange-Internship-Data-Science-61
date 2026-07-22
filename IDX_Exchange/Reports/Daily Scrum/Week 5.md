# Wednesday Meeting

## Questions:
- Hyperparameter testing
	- Amy: GridSearch, RandomSearch
	- This week seems like a really approachable way to start testing hyperparameters
- 

## Progress:

|              | Current Progress                                                                                                                                                                                                                                                                                                               | TO-DO                                                                                                                                                                                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cici Xiu     | Prepared metrics and such. Random forest was a lot better here, probably because of data cleaning (maybe see how she does it as reference!!)                                                                                                                                                                                   |                                                                                                                                                                                                                                                                           |
| Amy Trinh    | Edited preprocessing (removed extreme outliers, improved r2 for baseline model, 0.84 now!)<br><br>12 months still seemed to work the best. Only 1/2 of the models were trained correctly. <br><br>Linear regression > Decision Tree > Random Forest (randomized search for tuning)<br><br>Kept everything in the 95 percentile |                                                                                                                                                                                                                                                                           |
| Wenxin Cui   | Absent                                                                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                           |
| Anh Tran     |                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                                           |
| Lynne Nguyen | Attempted Decision tree and random forest. <br><br>                                                                                                                                                                                                                                                                            | I don't think I tuned my hyperparameters properly so I'll try to automate them next week, in addition to feature engineering. I'm graduating in two weeks so I haven't been able to spend much time on the internship but I'll have a lot more time once school lets out. |
| Yujian Tan   | Decision tree and random forest, but didn't do much hyperparameter tuning. As expected, performed a lot better. <br><br>Linear regression outperformed both models though (possibly because of hyperparameter tuning and one-hot encoding)                                                                                     |                                                                                                                                                                                                                                                                           |
| Ngo Tran     | Did imputation before the split, so reprocessed data and regression performed a lot better!!<br><br>Random Forest seems to                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                           |
# Report
## Todo
- Try Decision Tree and Random Forest regressors. 
- Compare their test R² against baseline. 
- Document model behavior (strengths/weaknesses). 
- Deliverable: 04_model_comparison.ipynb
	- Also improve my pipelines. Didn't have time for it this week so I'll probably have to do that next week.

## Progress
1. Fitted data to regression tree using sklearn's Decision Tree Regressor. 
	1. After one round of testing, it was pretty obvious that the model was completely overfitted. 
2. 

## Research
1. Decision Trees:
	- CART seems like the only viable tree here upon early research
2. Random Forest:
	- 