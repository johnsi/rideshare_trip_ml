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
   <p>Regression Models:<br>
   &emsp; Following regression models are used for the training and prediction of the trip duration,</p>
   <p>&emsp; Lasso Regressor:<br>
   &emsp; &emsp;The scaled data was trained on the Lasso model with polynomial feature of degree 3.<br>
   &emsp; &emsp; The model achieved the testing score of 58%</p>
   <p>&emsp; Rendom Forest Regressor:</p>
   <p>&emsp; Decision Tree:</p>
      
   

    
