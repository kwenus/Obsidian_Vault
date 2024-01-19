#таблицыSQL #SQL 

```sql
- создание таблицы:
CREATE TABLE [название таблицы] ([название столбца, тип данных, ограничение]);

если есть риск, что такая таблица уже есть добавляем:
CREATE TABLE IF NOT EXIST [название таблицы] ([название столбца, тип данных, ограничение]);

- пример:
CREATE TABLE student (id SERIAL PRIMARY KEY, name VARCHAR(60) NOT NULL, age INTEGER NOT NULL);
- если ошибки нет, выводит:
CREATE TABLE

- изменение названия столбца таблицы:
ALTER TABLE [название таблицы] 
RENAME [название столбца] 
TO [на что изменить];

пример:
ALTER TABLE student 
RENAME name TO surname;
если ошибки нет, выводит:
ALTER TABLE

- добавление нового столбца в таблицу:
ALTER TABLE [название таблицы] 
ADD [название столбца] [тип данных];

ALTER TABLE student 
ADD group_number integer NOT NULL;


- удалить таблицу:
DROP TABLE [название таблицы]
- если ошибки нет, выводит:
DROP TABLE
```
