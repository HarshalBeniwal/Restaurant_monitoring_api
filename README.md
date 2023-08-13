
# Soultion: - 

- Tech used: 
Python Django framework and PostgreSQL database.

# Step-by-step process for calculating uptime and downtime over the past 24 hours:

1. Initialize a dictionary called `uptime_downtime_stats` with keys "uptime," "downtime," and "unit." Set the values for "uptime" and "downtime" to 0, and "unit" to "hours."

2. Calculate the day one day before the current day, referred to as `previous_day`. If the current day is Monday (0), set `previous_day` to Sunday (6).

3. Check if the store was operational during the last 24 hours, from `previous_day` to `current_day`, at the present time (`current_time`). This involves querying the store's timings to determine if any entries match the specified day and time.

4. If the store was closed throughout the past 24 hours, return the initialized `uptime_downtime_stats`.

5. If the store was open during the last 24 hours, retrieve all status logs from the store's `status_logs` for the same time frame (from `utc_time - 1 day` to `utc_time`). Arrange the logs in chronological order based on their timestamps.

6. Iterate through each log in the retrieved `status_logs`:

   a. Check if the timestamp of the log falls within the store's business hours for that day (`log_in_store_business_hours`). This involves querying the store's timings to determine if any entries match the specified day and time.

   b. If the log is not within the store's business hours, skip it and proceed to the next log.

   c. If the status of the log is "active," increment the "uptime" value in `uptime_downtime_stats` by 1 hour.

   d. If the status of the log is not "active," increment the "downtime" value in `uptime_downtime_stats` by 1 hour.

7. The same methodology is applied for calculating uptime and downtime over the past one hour and the past one week.

This process provides a detailed breakdown of how to calculate uptime and downtime statistics over different timeframes, ensuring accurate tracking of the store's operational status.


# APIs :

1) Trigger Report

  http://localhost:8000/store/9200325206334396031/trigger_report/ 

   
2) Get Report
  http://localhost:8000/store/get_report/ 

	
