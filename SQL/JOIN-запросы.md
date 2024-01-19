![[join_requests]]


```sql
Основные виды JOIN
- [INNER] JOIN — в выборку попадут только те данные, по которым выполняются условия соединения. 
- LEFT [OUTER] JOIN — в выборку попадут все данные из таблицы A и только те данные из таблицы B, по которым выполнится условие соединения. Недостающие данные вместо строк таблицы B будут представлены NULL.
- RIGHT [OUTER] JOIN — в выборку попадут все данные из таблицы B и только те данные из таблицы А, по которым выполнится условие соединения. Недостающие данные вместо строк таблицы A будут представлены NULL.
- FULL [OUTER] JOIN — в выборку попадут все строки таблицы A и таблицы B. Если для строк таблицы A и таблицы B выполняются условия соединения, то они объединяются в одну строку. Если данных в какой-то таблице нет, то на соответствующие места вставляются NULL.
- CROSS JOIN — объединение каждой строки таблицы А с каждой строкой таблицы B

* Примеры
- выведем имена, фамилии и адреса всех сотрудников
SELECT first_name, last_name, address FROM staff
LEFT JOIN address ON staff.address_id = address.address_id;

- определим количество продаж каждого продавца
SELECT s.last_name, COUNT(amount) FROM payment
LEFT JOIN staff ON payment.staff_id = staff.staff_id
GROUP BY staff.last_name;

- посчитаем, сколько актеров играло в каждом фильме
SELECT title, COUNT(actor_id) actor_q FROM film
JOIN film_actor ON film.film_id = film_actor.film_id
GROUP BY film.title
ORDER BY actor_q DESC;

- сколько копий фильмов со словом Super в названии есть в наличии
SELECT title, COUNT(inventory_id) FROM film f
JOIN inventory i ON f.film_id = i.film_id
WHERE title LIKE '%Super%'
GROUP BY title;

- выведем список покупателей с количеством их покупок в порядке убывания
SELECT c.last_name n, COUNT(p.amount) amount FROM customer c
LEFT JOIN payment p ON c.customer_id = p.customer_id
GROUP BY n
ORDER BY amount DESC;

- выведем имена и почтовые адреса всех покупателей из России
SELECT c.last_name, c.first_name, c.email FROM customer c
JOIN address a ON c.address_id = a.address_id
JOIN city ON a.city_id = city.city_id
JOIN country co ON city.country_id = co.country_id
WHERE country = 'Russian Federation';

- фильмы, которые берут в прокат чаще всего
SELECT f.title, COUNT(r.inventory_id) count FROM film f
JOIN inventory i ON f.film_id = i.film_id
JOIN rental r ON i.inventory_id = r.inventory_id
GROUP BY f.title
ORDER BY count DESC;

- суммарные доходы магазинов
SELECT s.store_id, SUM(p.amount) sales FROM store s 
JOIN staff st ON s.store_id = st.store_id
JOIN payment p ON st.staff_id = p.staff_id
GROUP BY s.store_id;

- найдем города и страны каждого магазина
SELECT store_id, city, country FROM store s 
JOIN address a ON s.address_id = a.address_id
JOIN city ON a.city_id = city.city_id
JOIN country c ON city.country_id = c.country_id;

- выведем топ-5 жанров по доходу
SELECT category.name, SUM(payment.amount) revenue FROM category 
JOIN film_category ON category.category_id = film_category.category_id
JOIN inventory ON film_category.film_id = inventory.film_id
JOIN rental ON inventory.inventory_id = rental.inventory_id
JOIN payment ON rental.rental_id = payment.rental_id
GROUP BY category.name
ORDER BY revenue DESC 
LIMIT 5;
```