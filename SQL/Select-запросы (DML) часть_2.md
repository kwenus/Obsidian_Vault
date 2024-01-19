#SQL #select-запросы
```sql
* Агрегирующие функции (выполняют вычисления над значениями в столбце, результатом вседа является одно число)
- их только пять: MIN, MAX, SUM, AVG, COUNT.
- синтаксис: функция(название столбца)

*MIN и MAX
- найдем максимальную стоимость проката
SELECT MAX(rental_rate) FROM film;
- можно найти сразу и минимальную:
SELECT MAX(rental_rate), MIN(rental_rate) FROM film;

*AVG (среднее значение)
- посчитаем среднюю продолжительность фильма
SELECT AVG(length) FROM film;

* COUNT (количество строк в столбце)
- сколько уникальных имен актеров?
SELECT COUNT(DISTINCT first_name) FROM actor
- что бы узнать сколько вообще актеров:
SELECT COUNT(first_name) FROM actor
- что бы просто посчитать строки в столбце:
SELECT COUNT(*) FROM actor

* SUM (сумма по строкам в столбце)
- посчитаем сумму и средние продажи по конкретному продавцу
SELECT SUM(amount), AVG(amount) FROM payment
WHERE staff_id = 1; 


* Вложенные запросы (ограничений по вложенности нет)
- найдем все фильмы с продолжительностью ваше среднего
- так работать не будет (тк вычисление происходит после фильтрации)
SELECT title, length  FROM film
WHERE length >= AVG(length);
- нужно вот так (вначале вычисляется нужное значение, потом идет фильтрация)
SELECT title, length FROM film
WHERE length >= (SELECT AVG(length) FROM film);

- найдем названия фильмов, стоимость проката которых не максимальная
SELECT title, rental_rate FROM film
WHERE rental_rate < (SELECT MAX(rental_rate) FROM film)
ORDER BY rental_rate DESC;


* GROUP BY - Группировка по одному столбику:
- посчитаем количество актеров в разрезе фамилий (найдем однофамильцев)
SELECT last_name, COUNT(*) FROM actor
GROUP BY last_name
ORDER BY COUNT(*) DESC;

- посчитаем количество фильмов в разрезе рейтингов (распределение рейтингов)
SELECT rating, COUNT(title) FROM film
GROUP BY rating
ORDER BY COUNT(title) DESC;

- найдем максимальные продажи в разрезе продавцов
SELECT staff_id, MAX(amount) FROM payment
GROUP BY staff_id;

* Группировка по нескольким столбикам:
- найдем средние продажи каждого продавца каждому покупателю
SELECT staff_id, customer_id, AVG(amount) FROM payment
GROUP BY staff_id, customer_id
ORDER BY AVG(amount) DESC;

- можно вначале отфильтровать с помощью WHERE (но не наоброт!)
- найдем среднюю продолжительность фильма в разрезе рейтингов в 2006 году (здесь вначале фильтруем по году, потом группируем)
SELECT rating, AVG(length) FROM film
WHERE release_year = 2006
GROUP BY rating;


* HAVING (тоже самое что и WHERE, только после группировки)
- отберем только фамилии актеров, которые не повторяются
SELECT last_name, COUNT(*) FROM actor
GROUP BY last_name
HAVING COUNT(*) = 1;

- отберем и посчитаем только фамилии актеров, которые повторяются
SELECT last_name, COUNT(*) FROM actor
GROUP BY last_name
HAVING COUNT(*) > 1
ORDER BY COUNT(*) DESC;

- найдем фильмы, у которых есть Super в названии 
- и они сдавались в прокат суммарно более, чем на 5 дней
SELECT title, SUM(rental_duration) FROM film
WHERE title LIKE '%Super%'
GROUP BY title
HAVING SUM(rental_duration) > 5;


* ALIAS (псевдонимы для столбиков)
- предыдущий запрос с псевдонимами (в фильтре WHERE имя столбика пишется полностью, тк он работает до извлечения информации)
SELECT title AS t, SUM(rental_duration) AS sum_t FROM film AS f
WHERE title LIKE '%Super%'
GROUP BY t
HAVING SUM(rental_duration) > 5;

- ключевое слово AS можно не писать
SELECT title t, SUM(rental_duration) sum_t FROM film f
WHERE title LIKE '%Super%'
GROUP BY t
HAVING SUM(rental_duration) > 5;
```
