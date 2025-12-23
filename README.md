# Vehicle Rental System

### Query 1: JOIN

```
select booking_id,u.name as customer_name, v.name as vehicle_name, start_date,end_date,b.status from bookings as b
  inner join users as u on b.user_id=u.user_id
  inner join vehicles as v on b.vehicle_id=v.vehicle_id;

```
This JOIN query connects the bookings table with the users and vehicles tables to retrieve complete booking information along with the customer name and vehicle name.

The query matches the user_id in the bookings table with the user_id in the users table, and matches the vehicle_id in the bookings table with the vehicle_id in the vehicles table.