# Vehicle Rental System

### Query 1: JOIN

```sql
select booking_id,u.name as customer_name, v.name as vehicle_name, start_date,end_date,b.status from bookings as b
  inner join users as u on b.user_id=u.user_id
  inner join vehicles as v on b.vehicle_id=v.vehicle_id;

```
This query joins the bookings table with the users and vehicles tables. The user_id from the bookings table is matched with the user_id in the users table to get customer details. Similarly, the vehicle_id from the bookings table is matched with the vehicle_id in the vehicles table to get vehicle details. As a result, the query returns complete booking information along with related user and vehicle data.

### Query 2: EXISTS
```sql
select * from vehicles as v where not exists(
  select 1 from bookings as b where b.vehicle_id = v.vehicle_id
);
```
This query uses the NOT EXISTS condition to check whether a vehicle appears in the bookings table. If no matching booking record is found for a vehicle, it is included in the result. This helps identify vehicles that are still unused or available for booking.

### Query 3: WHERE

```sql
select * from vehicles where type='car' and status='available';
```
This query filters the vehicles table using the WHERE clause. It selects only those records where the vehicle type is car and the status is available. The result shows all cars that are currently available for booking.

### Query 4: GROUP BY and HAVING

```sql
select name as vehicle_name,count(booking_id) as total_bookings from vehicles as v
inner join bookings as b on v.vehicle_id=b.vehicle_id
group by name 
having count(booking_id) > 2;
```
This query joins the vehicles and bookings tables and groups the records by vehicle name. The COUNT function calculates the total number of bookings for each vehicle. The HAVING clause is then used to filter the grouped results, showing only vehicles that have been booked more than two times.