# Project Instructions


# Optimization of the Water Pump Portfolio and Seasonality Analysis for Sales Maximization

### Business Context:
- A water pump manufacturing company is facing challenges in managing its product portfolio and planning its production. The commercial management needs to better understand sales behavior to make strategic decisions regarding:

1. Which products maintain consistent performance;
2. Whether there is seasonality in sales;
3. How to optimize the product mix.

### Business Problem:
The company needs to reduce operational costs and increase profit margin through better production planning and inventory management. Currently, there are problems with:

1. Excess inventory of some models;
2. Stockouts in others;
3. Difficulty in forecasting demand;
4. Possibly non-optimized product mix.

### Business Questions to be Answered:

1. Is there seasonality in the sales of different product groups?
2. Which products are most relevant in terms of revenue?
3. How is the distribution of sales behaving among the different product groups?
4. Are there products with a trend of growth or decline in sales?
5. What is the correlation between the quantity sold and the revenue value per product group?


### Project Objectives:

1. Perform exploratory data analysis;
2. Identify seasonality patterns;
3. Segment products by performance;
4. Create visualizations that support decision-making.


### Propose data-driven recommendations for portfolio optimization
Expected Impact:

1. 15% reduction in inventory costs;
2. 10% increase in profit margin;
3. 20% improvement in production planning accuracy;
4. 30% reduction in stockouts.


### Deliverables:

1. Interactive dashboard with key KPIs;
2. Trend and seasonality analysis;
3. Product segmentation by performance;
4. Data-driven strategic recommendations.


### Complete project documentation
This problem is interesting for a portfolio because:

1. It demonstrates exploratory analysis capability;
2. It works with temporal data;
3. It has practical business application;
4. It allows showcasing visualization skills;
5. It has the potential for the use of different analytical techniques.


## Exploratory Data Analysis (EDA)


![logo](images/1_group_counts.png)






![logo](images/2_sales_orderreturn.png)





![logo](images/3_groupcode_sales_orderreturn.png)






![logo](images/4_orderreturn_year.png)





![logo](images/5_orderreturn_month.png)




![logo](images/6_groupcode_sales_quarter.png)




![logo](images/7_correlationmap.png)


### **Summary of the main EDA Findings**

1. 'MOTOBOMBA_APP' group code is by far the group code that can be considered for further modeling analysis, due to the fact that it has much more data available than the other groups.
2. There is no weekend data in this dataset.
3. There are much more sold items than items order return, then the last one should be dropped out of the data.
4. Items are in general much more sold on November and December, followed by a decrease trend on January.
5. At 2018, 2019 there have been the largest amount of items sold in this database, followed by a decrease that might be related to the COVID-19 pandemics.
6. According to the correlation matrix, there are very weakly correlated features in this dataset.

## Time-Series Machine Learning Modeling

The following figure shows the prediction by using *ARIMA* modeling for time-series, from which it is clear that the ARIMa models do not work reasonably well on this data.

![logo](images/8_ARIMA_modeling.png)

The picture below shows the predictions of a **XG Boost** regressor in the testing set, which displayed an *accuracy* of **88.02%**, evidencing a great fitting to the data.

![logo](images/9_xgboost_test.png)

For the above XG Boost regressor, the picture below shows the importance of features to the overall predictions of the model. One can notice that two rolling mean related features are the most important ones.

![logo](images/10_xgboost_importance.png)

The picture below shows the predictions of a **Random Forest** regressor in the testing set, which displayed an *accuracy* of **91.69%**, evidencing a great fitting to the data.

![logo](images/11_rf_test.png)

For the above Random Forest regressor, the picture below shows the importance of features to the overall predictions of the model. One can notice that rolling mean related features are the most important ones.

![logo](images/12_rf_importance.png)

Finally, the picture below shows the predictions on the testing set for the "normal" way (as it was performed previously - red line) and for the iterative approach (it uses the current prediction as a feature for the next one - green line). Interestingly, the iterative approach has an almost perfect agreement to the testing data until November 2023, while the "normal" approach does not fit so well in the beginning, but after November 2023 it still keep yielding good results.


![logo](images/13_iterativeprocess.png)

## Summary of the main ML Forecasting Findings

1. **Random Forest** was shown to be the best model, having presented an accuracy on the testing data above **91%**.
2. Rolling mean related features are the most predictive features for both Random Forest and XG Boost models.
3. ARIMA models seem to not work reasonably well on this data.
