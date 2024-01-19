#SQL
```sql
*DDL (Data Definition Language): управление таблицами
CREATE, ALTER, DROP   
*DML (Data Manipulation Language): управление данными в таблицах
SELECT, INSERT, UPDATE, DELETE
*TCL (Transaction Control Language): управление транзакциями
COMMIT, ROLLBACK, SAVEPOINT 
*DCL (Data Control Language): управление пользователями и их правами
GRANT, REVOKE, DENY

- популярные типы данных DDL:
integer - целые числа - id integer
serial - целые числа с автоинкрементом - id serial  
numeric - десятичные числа - gpa numeric(3, 2)  
character varying` - строки ограниченной длины - name varchar(40)  
text - строки произвольной длины - message text  
date - дата (без времени) - birthday date
timestamp - дата + время - created_at timestamp  
boolean - булевые значений - active boolean  
jsonb - JSON-поля - data jsonb

- Ограничения_SQL
primary key = Первичный ключ, обязывает поле быть уникальным и не пустым 
id serial primary key not null = Значение не может быть пустым (не может отсутствовать)
name varchar(40) not null  
unique = Все значения в этом поле должны быть уникальным 
tag varchar(80) unique  
check = Добавить проверку значения на описанное условие 
price numeric check(price > 0)  
foreign key = Внешний ключ, обязывает значение соответствовать значению из другой таблицы
product_id integer references
```

