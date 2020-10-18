# PyBer_Analysis

## Overview of PyBer Analysis
The purpose of this assignment is to have a understand of which business line: Rural, Suburban, or Urban is doing better. Using data and trends to improve access to ride-sharing services and determine affordability for underserved neighborhoods. It is critical to be able pull and understand data to be able to report and explain the data effectively.
This report is to create a summary DataFrame to provide the Total Rides, Total Drivers, Total Fares, Average Fare per Ride, and Average Fare per Driver for each city. Second, a multiple-line plot to show the sum of the fares for each city type by using the Pandas and Matplotlib libraries to plot the sum of the fares for each city type.

## Results
I have received two set of data the first data set for three city types and cities: Urban, Suburban, and Rural. The second set of data for rides in each city. I inspect the data for how many columns and rows are there, What types of data are present, is the data clean. Once I studied the data set I then find how many riders are in each individual city, total drivers, total fares in each city, average fare per ride, and average fare per driver. I then created DataFrames and graphs.

Code to convert and Merge the data together:

    Import matplotlb.pyplot as plt
    Import pandas as pd
    city_data_to_load = “./Resources/city_data.csv”
    ride_data_to_load = “./Resources/ride_data.csv”
    pyber_data_df = pd.merge(ride_data_df, city_data_df, how="left", on=["city "])
    pyber_data_df

Running this code now allow you to create the DataFrames for: 
Total rides by city type

    city_data = pyber_data_df.groupby(["type"]).count()["ride_id"]
    city_data
       type
       Rural: 78
       Suburban: 490
       Urban: 2405
       Name: driver_count, dtype: int64
With this data you can which area had the most rides and the least amount of rides. Which would be Rural having the least amount and Urban having the most.
                  
Total drivers by city type

    driver_count = city_data_df.groupby(["type"]).sum()["driver_count"]
    driver_count
      type
      Rural         78
      Suburban     490
      Urban       2405
      Name: driver_count, dtype: int64
In this data you can see that Urban also has the most drivers.

Total Fares

    sum(city_fare_count)
      63538.6400000001
This is just the total amount of fares from the cities.

Average Fare per ride

    city_avg_fare = pyber_data_df.groupby(["type"]).mean()["fare"]
    city_avg_fare
      type
      Rural       34.623440
      Suburban    30.970128
      Urban       24.525772
      Name: fare, dtype: float64
This is the average cost of fares in each area.

Average Fare per driver

    driver_avg = city_fare_count / driver_count
    driver_avg
      type
      Rural       55.486282
      Suburban    39.502714
      Urban       16.571468
      dtype: float64
This shows what the average cost the driver charged.

Total Fares by city type 

    city_fare_count = pyber_data_df.groupby(["type"]).sum()["fare"]
    city_fare_count
      type
      Rural        4327.93
      Suburban    19356.33
      Urban       39854.38
      Name: fare, dtype: float64
This is the total amount of fares by city types.

# Summary
I used the following code to create the Summary:

    pyber_summary_df=pd.DataFrame({
       'Total Riders':city_data,
        'Total Drivers':driver_count,
        'Total Fares':city_fare_count,
        'Average Fare per Rider':city_avg_fare,
        'Average Fare per Driver':driver_avg})
    pyber_summary_df 
   ![Data](https://github.com/alainacox/PyBer_Analysis/blob/main/Resources/data_summary.png)

 
My recommendation to our CEO is to send additional resources to urban then suburban and rural throughout the year. Urban is making the most revenue due to higher demand. The reasons could be more business convention centers or more economic for consumer to catch share rides than owning a car. As well as the rides in the urban area tend to cost less than the rural area. Focus on Urban business line will drive better revenue to company. Rural is the lowest line in making money, but we still need to maintain our present as a way to adverstise and capture smaller market shares.
