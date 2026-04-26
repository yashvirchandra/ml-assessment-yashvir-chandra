B1. PROBLEM FORMULATION

(a). In this case, the main goal is to figure out which promotion works best for each store in a given month so that the number of items sold is maximised. So, I would define the target variable as the total number of items sold per store per month.

To predict this, I would use features like store size, location type (urban, semi-urban, rural), monthly footfall, competition in the area, and customer demographics. Along with that, the type of promotion being used is also very important. Time-based factors like month, weekends, and festivals should also be included because they can strongly affect shopping behaviour.

Since we are predicting a numerical value (items sold), I think this is a regression problem under supervised learning. We already have past data with known outputs, so the model can learn patterns and use them to make future predictions.
 

(b). The company is currently using total sales revenue  to measure performance, but I feel that might not be the best choice here. Revenue depends on prices, discounts, and the type of products sold. For example, a heavy discount might increase the number of items sold but reduce overall revenue.

On the other hand, the number of items sold directly shows how effective a promotion is in attracting customers and increasing sales volume. Since the goal is to maximise sales through promotions, using items sold makes more sense.

This also shows an important idea in machine learning: the target variable should match the actual business goal. If we choose the wrong target, even a good model wont give useful results. 


(c). Using one single model for all 50 stores might not work well and would not be a good idea because stores in different locations behave very differently. For example, customers in urban areas might respond differently to promotions compared to rural areas.

Instead, I would either group the stores based on similar characteristics (like location or customer type) and build separate models, or use a hierarchical model that can capture both overall patterns and store-specific behaviour. This way, the model can better adjust to local differences.


B2. DATA AND EDA STRATEGY

(a). The data is coming from four different tables, so the first step would be to combine them properly. I would join  the transactions table with the store attributes using the store ID, Then I would link the promotion details using the promotion ID, and finally join the calender table using the date column.

After joining everything, I would aggregate the data at a monthly level for each store. So basically, one row in the final dataset would represent one store for one month. In that row, I would include total items sold, total transactions, and maybe average basket size. I would also include which promotion was used in that month along with calendar features like whether there were festivals or weekends.


(b). Before building any model, I would spend time exploring the data. First, I would look at how different promotions perform by plotting average items sold for each promotion type. This can give a basic idea of what works better.

Next, I would plot sales over time to check for trends or seasonality, like whether sales increase during festivals. I would also compare performance across stores using box plots to see how much variation exists between them.

Another useful step would be checking correlations between variables like footfall, promotions, and sales. This can help in understanding which factors are more important and should definitely be included in the modal. Overall, EDA helps in making better decisions before actually training the model.


(c). Since 80% of the transactions happened without any promotion, the dataset is quite imbalanced. This could cause the model to focus more on non promotion cases and ignore the effect of promotions.

To handle this, I would try techniques like balancing the dataset by increasing the proportion of promotion-related data or assigning more importance (weights) to those cases. This would help the model learn the impact of promotions more effectively.


B3. MODEL EVALUATION AND DEPLOYMENT 

(a). Because the data is time-based, I would not use a random train-test split. Instead, I would split the data based on time. For example, I could use the first 2.5 years of data for training and the last 6 months for testing.

A random split would mix past and future data, which is not realistic and can lead to incorrect results. In real life, we always predict the future using past data.

For evaluation, I would use metrics like MAE, RMSE, and R². MAE tells us the average error, RMSE gives more importance to large errors, and R² shows how well the model explains the data. Together, these metrics give a good understanding of model performance.


(b). If the model suggests different promotions for the same store in different months, I would try to understand why by looking at feature importance. This helps in identifying which factors are influencing the decision the most.

For example, in December, there might be festivals or holidays, so customers are already in a buying mood. In that case, something like a loyalty points bonus might work better. In March, which might be a slower month, a flat discount could be more effective in attracting customers.

I would explain this to the marketing team in simple terms, focusing on customer behaviour and seasonal patterns rather than technical details.


(c). For deployment, the trained model would first be saved in a file so that it can be reused without training it again every time. At the start of each month, new data would be collected and processed in the same format as the training data.

This data would then be passed into the model to generate promotion recommendations for each store. After that, it is important to monitor how well the model is performing by comparing predictions with actual results.

If the model’s performance starts dropping or if there are changes in customer behaviour, then the model should be retrained using updated data to keep it accurat