```sql
- WHERE
SELECT user_id, first_name, last_name
FROM users
WHERE first_name = 'Надежда';

- AND
SELECT user_id, first_name, last_name
FROM users
WHERE first_name = 'Михаил' AND last_name = 'Абрамов'

- boolean
SELECT user_id, first_name, last_name, agent
FROM users
WHERE first_name = 'Михаил' AND last_name = 'Абрамов' AND agent = true

- LIKE
SELECT user_id, first_name, last_name
FROM users 
WHERE first_name LIKE 'Вер%' AND last_name LIKE '%хор%'
ORDER BY user_id;

- DISTINCT 
SELECT DISTINCT first_name
FROM users
WHERE first_name LIKE 'И%';

- вычисления в SQL
SELECT estate_object_id
FROM estate_object
WHERE object_type_id = 1 AND living_area + kitchen_area = total_area;

- OR
SELECT estate_object_id, object_type_id, year_of_construction, number_of_rooms
FROM estate_object
WHERE number_of_rooms = 4 AND (object_type_id = 2 AND year_of_construction = 2005 OR object_type_id = 4 AND year_of_construction BETWEEN 2001 AND 2003);

- запросы с датами
SELECT advertising_id, created_at FROM advertising
WHERE created_at BETWEEN '2022-01-03 00:00:01' AND '2022-01-05 23:59:59';

- ORDER BY и LIMIT
SELECT advertising_id, amount, created_at, status
FROM advertising
WHERE status = 'Активно' AND EXTRACT (YEAR FROM created_at) = 2022
ORDER BY amount DESC
LIMIT 5;

- UPPER
SELECT UPPER(city_name) FROM city
```
