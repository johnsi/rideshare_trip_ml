# Rideshare Data Analysis and Modeling

### Executive summary

**Project overview and goals:** 
The goal of this project is to predict the trip duration of any taxi trip taken from the pickup point to destination.
We will be using both regression and classification algorithms to predict the trip duration for the given data point. 
We will also be locally analyzing this model and evaluating its class prediction process for individual trip.

**Data Summary:** <br>
The dataset has the taxi trip information which includes,<br>
     <p> &emsp;id - a unique identifier for each trip<br>
      &emsp;vendor_id - business provider id. possible values are 0 or 1<br>
      &emsp;pickup_datetime - Trip pickup time<br>
      &emsp;dropoff_datetime - Trip end time<br>
      &emsp;passenger_count - Number of passengers in the vehicle<br>
      &emsp;pickup_longitude - Trip start longitude<br>
      &emsp;pickup_latitude - Trip start latitude<br>
      &emsp;dropoff_longitude - Trip end longitude<br>
      &emsp;dropoff_latitude - Trip end latitude<br>
      &emsp;pickup_district - Trip pickup district<br>
      &emsp;dropoff_district - Trip end district<br>
      &emsp;store_and_fwd_flag - possible values y or n<br>
      &emsp;day_period - possible values Afternoon,Night,Morning,Evening<br>
      &emsp;month : Month the trip was taken. Metric from pickup_datetime<br>
      &emsp;season : Season the trip was taken.Metric from pickup_datetime<br>
      &emsp;weekday_or_weekend : Weekday trip or weekend trip<br>
      &emsp;regular_day_or_holiday : Regular day or holiday trip<br>
      &emsp;day_name : day name<br>
      &emsp;pickup_hour: on which hour of the day the trip started<br>
      &emsp;financial_quarter: financial quarter<br>
      &emsp;trip_duration - Trip duration in seconds<br>
      &emsp;distance - Trip distance metric calculated from start lat/long and end lat/long<br></p>
	1. Initially I started the exploration with 7 days of trip data and then shrinked it to 1 day due to the time taken to fit each model<br>
  	2. Dropped the rows with null values and removed the outliers<br>
   	3. Majority of the trip started from Manhatten<br>
        4. Trip start during the mid night in weekends is higher than weekdays<br>
	5. Created a new field called 'distance' by subtracting  pickup_latitude.pickup_longitude from dropoff_longitude/dropoff_latitude<br>
	6. Correlation metrix showed positive correlation between trip duration and distance<br>
 	7. PCA analysis shown 12 important features to use for model which includes,<br>
  	'vendor_id', 'passenger_count', 'pickup_longitude', 'pickup_latitude',<br>
       'dropoff_district', 'dropoff_neighbourhood', 'dropoff_geonumber',<br>
       'day_period', 'month', 'year', 'pickup_hour', 'day_name',<br>
       'financial_quarter', 'distance' <br>

### Methodology <br>
   To predict the duration of the trip the models were trained on the training set and validated with the test set.<br>
   <p><b>Regression Models:</b></b><br>
   &emsp; Following regression models are used for the training and prediction of the trip duration,</p>
   <p>&emsp;<b> Lasso Regressor:</b><br>
&emsp; &emsp;Lasso is a modification of linear regression, where the model is penalized for the sum of absolute values of the weights.<br>
   &emsp; &emsp;The scaled data was trained on the Lasso model with polynomial feature of degree 3.<br>
   &emsp; &emsp;The model achieved the testing score of 58%.</p>
   <p>&emsp;<b> Rendom Forest Regressor:</b><br>
   &emsp;&emsp;Random Forest Regression is a supervised learning algorithm that uses ensemble learning method for regression. <br>&emsp;&emsp;Ensemble learning method is a technique that combines predictions from multiple machine learning algorithms to make a more accurate prediction than a single model.<br>
   &emsp;&emsp;Test accuracy metrix for Random forest is 60%.</p>
   <p>&emsp;<b> Decision Tree:</b><br>
     &emsp;&emsp; Decision tree with max_depth of 5 on 13 features achieved 57% accuracy on the test data.</p></p>
<p><b>Classification Models:</b><br>
	<p>&emsp;&emsp;&emsp;I added a categorical field called 'trip_category' on the dataset. <br>
 	&emsp;&emsp;&emsp;trip_duration between 1 and 350, trip_category is low.<br>
  	&emsp;&emsp;&emsp;trip_duration between 351 and 700, trip_category is medium.<br>
   	&emsp;&emsp;&emsp;trip_duration between 700  and above, trip_category is high.<br>
    &emsp;&emsp;&emsp;I am using this new field as a target variable for the classification models.<br></p>
    <p>&emsp;&emsp; Following classification models are used for the training and prediction of the trip category<br>
    <p>&emsp;&emsp;<b>Logistic Regression:</b><br>
	   &emsp;&emsp;&emsp; A pipeline object is created to standardize the data using TF-IDF and instantiate a Logistic Regression model.<br>
	    &emsp;&emsp; &emsp;The penalty has been set to l1 and l2. The best model has l2 penalty and an intercept term.<br>
	    &emsp;&emsp;&emsp; The accuracy score on the testing dataset is 66%
     </p>
    <p>&emsp;&emsp;<b>Decision Trees:</b><br>
    &emsp;&emsp;&emsp;A pipeline object is created to standardize the data using TF-IDF and instantiate a Decision Tree model.<br>
	    RandomizedSearchCV is used to find <br>
	    &emsp;&emsp;&emsp;  the optimal tree criterion, with the options being ['gini', 'entropy'], <br>
	    &emsp;&emsp; &emsp; max depth (options: [1,2,3,4,5])<br>
     	     &emsp;&emsp;&emsp; The accuracy score on the testing dataset is 68%.<br>
    </p>
    <p>
    </p>&emsp;&emsp;<b>K-Nearest Neighbor:</b><br>
    &emsp;&emsp;&emsp; n_neighbors set as (1,2,3,4,5)<br>
    &emsp;&emsp;&emsp;Weights set as uniform and distance<br>
    &emsp;&emsp;&emsp;Metric set to euclidean,manhattan<br>
    &emsp;&emsp;&emsp;Model overfitted on the training data and test accuracy is 60%.<br>
    </p>
    <p>&emsp;&emsp;<b>Support Vector Machine:</b><br>
	    &emsp;&emsp;&emsp;Kernal set to linear and rbf<br>
	    &emsp;&emsp;&emsp;Test accuracy 66%<br>
    </p>

</p>
<p><b>Conclusion</b> <br>
	When comparing the test accuracy of the Regression models with Classification Models, Classification models prediction is better than Regression models. 
Logistic Regression,Decision Trees and SVM almost predicted the same result. KNN looks overfitted in the training dataset.
Decision Tree performed better in the Regression models.
Finally, With the proper tuning of Hyperparameter we can improve these models performance in the future. 
My recommendation is to use Logistic Regression in classification model and use Decision tree for Regression Model.</p>
<p>
	[Link to notebook] http://localhost:8889/notebooks/jupiter_dir/nyc/NYC%20Taxi%20Trip%20Analysis.ipynb<br>
 
	[Link to download data]
</p>
   

    
