Portuguese Bank Term Deposit Prediction

Predicting which customers will subscribe to a term deposit after a bank's direct phone-call marketing campaign, and turning the findings into practical recommendations for the marketing team.

Domain: Finance / Banking
Data: Direct marketing campaigns of a Portuguese bank, May 2008 – Nov 2010 (41,188 calls, 20 inputs, target y)
Notebook: Portuguese_Bank_Term_Deposit_Prediction.ipynb

What's in the notebook
Data analysis report: data quality, target imbalance, numeric and categorical drivers, correlations, key insights
Predictive model: preprocessing, five candidate models, threshold selection, tuning, decile lift, feature importance
Marketing recommendations: data-driven suggestions for prioritising and timing calls
Model comparison report: side-by-side metrics and a production recommendation
Challenges report: problems met in the data, the technique used for each, and why
Key results
Model	ROC-AUC	PR-AUC	Recall (yes)	Precision (yes)
LightGBM	0.811	0.486	0.600	0.479
XGBoost	0.810	0.481	0.593	0.481
Random Forest	0.808	0.482	0.589	0.477
Decision Tree	0.800	0.460	0.557	0.481
Logistic Regression	0.800	0.446	0.559	0.460
Only 11.3% of calls ended in a subscription, so models are judged on PR-AUC, recall and precision rather than accuracy.
duration (call length) is excluded from the model because it is unknown before a call. Including it would lift ROC-AUC to 0.95, but the model would not be usable in practice.
Ranked by the model, the top 10% of customers subscribe at 53.6% (4.8x the average), and the top 20% contain about two-thirds of all subscribers.
Main recommendations
Call the highest-scoring customers first.
Re-contact clients from a previously successful campaign (65% subscribed).
Prefer mobile numbers (14.7% vs 5.2% for landline).
Cap repeat attempts at about 3–4 per customer.
Spread calls across the year instead of concentrating them in May.
Limitations
A stratified random split was used, but the data is time-ordered and the economic features partly stand in for the calendar period. A time-based validation is the recommended next step.
High subscription rates in low-volume months may reflect who was called rather than the month itself.
Tech stack

Python, pandas, NumPy, scikit-learn, LightGBM, XGBoost, matplotlib, seaborn, Jupyter

How to run
bash
pip install pandas numpy scikit-learn lightgbm xgboost matplotlib seaborn jupyter
# place bank-additional-full.csv in the same folder as the notebook
jupyter notebook Portuguese_Bank_Term_Deposit_Prediction.ipynb

The full run takes about 4–5 minutes.

Data source

S. Moro, P. Cortez and P. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, 2014. doi:10.1016/j.dss.2014.03.001
