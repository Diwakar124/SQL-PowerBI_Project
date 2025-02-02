# SQL-PowerBI_Project
# Sql Problem solve 
# 1. Retrieve all successful bookings:
create view Successful_Bookings as
select * from bookings
where Booking_status = 'Success';

# 2. Find the average ride distance for each vehicle type:
select Vehicle_Type, avg(Ride_Distance)
as avg_distance from bookings
group by  Vehicle_Type;


# 3. Get the total number of cancelled rides by customers:
 select count(*) from bookings
 where Booking_status = 'Canceled by Customer';


 # 4. List the top 5 customers who booked the highest number of rides
  select Customer_ID , count(Booking_ID) as total_ride
  from bookings
  group by Customer_ID
  order by total_ride desc limit 5;

  # 5. Get the number of rides cancelled by drivers due to personal and car-related issues:
  select count(*) from bookings
  where Canceled_Rides_by_Driver = 'Personal & Car related issue';

  #  6. Find the maximum and minimum driver ratings for Prime Sedan bookings:
  select max(Driver_Ratings) as max_rating, min(Driver_Ratings) as min_rating
  from bookings
  where Vehicle_Type = 'Prime Sedan';

  #  7. Retrieve all rides where payment was made using UPI:
select * from bookings
where Payment_Method = 'UPI';

# 8. Find the average customer rating per vehicle type:
select Vehicle_Type, avg(Customer_Rating) 
as avg_customer_rating from bookings
group by Vehicle_Type;

# 9. Calculate the total booking value of rides completed successfully:
select  sum(Booking_Value) as 
total_successful_ride from bookings
where Booking_status = 'Success'; 

# 10. List all incomplete rides along with the reason:
select Booking_ID, Incomplete_Rides_Reason 
as incomplete_ride from bookings
where Incomplete_Rides =  'yes';
  
