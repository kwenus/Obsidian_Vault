#SQL 
```sql
- INSERT
добавим новый курс
INSERT INTO course(name, description) 
VALUES('Python', 'Python с нуля');

- можно не перечислять атрибуты, но тогда придется указать их все в VALUES
(обязательно указывается номер id, без него ошибка)
INSERT INTO course 
VALUES(999, 'Java', 'Без описания');

- пример с нарушением внешнего ключа
INSERT INTO homeworktask(course_id, number, description) 
VALUES(999, 3, 'Описание задачи');

- чтобы добавить сразу несколько значений, передаем их в скобках через запятую
insert into genre (title) 
values ('indie'), ('rap'), ('classic')

- проверим
SELECT * FROM genre;

- UPDATE
обновляет значение в выбранной строке и столбце
UPDATE course 
SET description = 'Java с нуля' 
WHERE id = 999;

проверим
SELECT * FROM course 
WHERE id = 999;

- DELETE
DELETE FROM homeworktask 
WHERE id = 3;

- удалим запись о прокате
DELETE FROM course WHERE id = 999;

- проверим
SELECT * FROM course;
```
