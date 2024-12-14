# SocialMediaAdvertisement
Social Media Advertisement
Introduction:
The primary objective of this project was to investigate which factors most significantly influence the Return on Investment (ROI) of social media advertising campaigns and to develop a predictive model for ROI. The dataset comprised 300,000 records and 16 features, containing detailed information about various campaigns. Key features included Channel Used, Engagement Score, Acquisition Cost, Clicks, Impressions, as well as categorical features such as Campaign Goal, Location, and others. The initial hypothesis was that features like Engagement Score and Channel Used would have a substantial impact on ROI. The dataset was first examined and cleaned. Columns with numeric data stored as text were converted to numeric format. A thorough inspection confirmed the absence of missing values, and the data types were standardized.
Exploratory Analysis:
An initial analysis was performed to understand the relationships between the features and ROI. A correlation matrix revealed that Engagement Score had the strongest positive correlation with ROI (0.35), followed by Clicks (0.19) and Impressions (0.17). Features such as Year and Language showed negligible correlations with ROI. These results supported the initial hypothesis that Engagement Score and Channel Used are critical determinants of ROI.
Model Development with Random Forest:
a.	Initial Model:
A Random Forest Regressor was selected to predict ROI. The dataset was split into training and testing sets, with 80% of the data used for training (240,000 records) and 20% for testing (60,000 records).
To improve model performance, GridSearchCV was used to tune hyperparameters:
•	The parameters explored included:
o	Number of trees (n_estimators): 100, 300
o	Tree depth (max_depth): 10, 15
o	Features per split (max_features): sqrt, log2
•	The optimal parameters identified were:
{'max_depth': 15, 'max_features': 'sqrt', 'n_estimators': 300}

b.	Results:
The optimized model achieved the following metrics:
•	Mean Absolute Error (MAE): 1.5884
•	R² Score: 0.3319
While the model explained approximately 33% of the variance in ROI, it also highlighted that the dataset lacks some key information to enhance prediction accuracy.
c.	Feature Importance:
Feature importance analysis revealed that:
•	Engagement Score contributed the most to ROI prediction, accounting for 36.9% of the importance.
•	Channel Used was the second most significant feature, contributing 29.9%.
•	Clicks (8.8%) and Impressions (6.9%) also played moderate roles. Conversely, features like Year, Language, and Campaign Goal showed minimal importance, indicating their potential irrelevance to the model.
Model Comparison with XGBoost:
To further validate the findings, the XGBoost model was implemented with the following parameters:
•	max_depth: 6
•	eta: 0.1
•	subsample: 0.8
•	colsample_bytree: 0.8
•	Boosting rounds: 100
The XGBoost model achieved comparable results:
•	MAE: 1.5896
•	R² Score: 0.3305
These results confirmed that while XGBoost is a robust model, it did not significantly outperform Random Forest for this dataset.

 
The two plots above compare the Actual vs Predicted ROI for the Random Forest and XGBoost models. While both models exhibit a similar pattern of predictions, the data points are scattered around the reference line, indicating moderate prediction accuracy. The similarity in scatter patterns reinforces that both models performed comparably, as evidenced by their MAE and R² values."
•	Random Forest shows weaker predictive performance, as the predicted values remain clustered around a fixed range.
•	XGBoost demonstrates relatively better predictions, but further improvements are still needed to reduce the deviation from the reference line.
optimizing the hyperparameters and exploring alternative evaluation methods is suggested to further improvements in the accuracy of the models.
Conclusions:
The analysis confirmed the hypothesis that key features such as Engagement Score and Channel Used have a significant impact on ROI. The Random Forest model, after optimization, demonstrated reasonable predictive power, with an R² score of approximately 33%. This indicates that while the model captured some patterns, it could not fully explain the variance in ROI, likely due to missing influential factors in the dataset.
The relatively low R² score suggests that some critical features affecting ROI were not included in the dataset. Potentially missing features include:
•	Precise advertising budget for campaigns
•	Type and quality of advertising content
•	User engagement metrics such as likes, shares, and comments
Additionally, some features such as Year and Language showed negligible relevance, implying they could be excluded to streamline the model further.
This project successfully demonstrated the viability of using machine learning models, particularly Random Forest, to predict ROI in social media advertising campaigns. The study identified critical features affecting ROI, such as Engagement Score and Channel Used, which could guide future advertising strategies. However, to achieve higher predictive accuracy, incorporating additional data and exploring advanced models is essential.
Recommendations for Improvement:
1.	Incorporating additional features: Future datasets should include variables like advertising budget, content type, and detailed user engagement metrics to improve the model's explanatory power.
2.	Using advanced modeling techniques: Models such as LightGBM or CatBoost could be tested for potentially better performance.
3.	Stratified analysis: Analyzing ROI separately for different advertising channels (e.g., Instagram, Facebook) or target audiences could reveal more nuanced patterns.
4.	Reducing feature noise: By removing irrelevant features identified in this analysis, model complexity and training time could be reduced without sacrificing performance.





