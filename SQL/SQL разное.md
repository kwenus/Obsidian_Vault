```sql
* экранирование символов - одинарная кавычка:
'The Go-Go''s'

* игнорировать регист при поиске - ilike:
select title from track
where title ilike '%my %';

* искать строки из одного слова (т.е. без пробелов):
select musician_name from musician
where musician_name not like '% %'

```
