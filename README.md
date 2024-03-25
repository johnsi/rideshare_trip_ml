# Rideshare Data Analysis and Modeling

### Executive summary

**Project overview and goals:** 
The goal of this project is to predict the trip duration of any taxi trip taken from the pickup point to destination.
We will be using both regression and classification algorithms to predict the trip duration for the given data point. 
We will also be locally analyzing this model and evaluating its class prediction process for individual trip.

**Data Summary:** <br>
The dataset has the taxi trip information which includes,<br>
      id - a unique identifier for each trip<br>
      vendor_id - business provider id. possible values are 0 or 1<br>
      pickup_datetime - Trip pickup time<br>
      dropoff_datetime - Trip end time<br>
      passenger_count - Number of passengers in the vehicle<br>
      pickup_longitude - Trip start longitude<br>
      pickup_latitude - Trip start latitude<br>
      dropoff_longitude - Trip end longitude<br>
      dropoff_latitude - Trip end latitude<br>
      pickup_district - Trip pickup district<br>
      dropoff_district - Trip end district<br>
      store_and_fwd_flag - possible values y or n<br>
      day_period - possible values Afternoon,Night,Morning,Evening<br>
      month : Month the trip was taken. Metric from pickup_datetime<br>
      season : Season the trip was taken.Metric from pickup_datetime<br>
      weekday_or_weekend : Weekday trip or weekend trip<br>
      regular_day_or_holiday : Regular day or holiday trip<br>
      day_name : day name<br>
      pickup_hour: on which hour of the day the trip started<br>
      financial_quarter: financial quarter<br>
      trip_duration - Trip duration in seconds<br>
      distance - Trip distance metric calculated from start lat/long and end lat/long<br>
	1. Initially I started the exploration with 7 days of trip data and then shrinked it to 1 day due to the time taken to fit each model
  2. 
