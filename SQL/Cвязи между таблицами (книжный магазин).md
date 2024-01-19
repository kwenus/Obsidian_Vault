#SQL
```sql
CREATE TABLE client (
client_id SERIAL PRIMARY KEY,
email VARCHAR(255) NOT NULL,
address VARCHAR(255) NULL,
phone VARCHAR(15) NULL,
sex SMALLINT NOT NULL);`

CREATE TABLE author (
author_id SERIAL PRIMARY KEY,
name VARCHAR(100) NOT NULL,
birthday date NOT NULL);`

CREATE TABLE book (
book_id SERIAL PRIMARY KEY,
title VARCHAR(255) NOT NULL,
price DECIMAL(10, 2) NOT NULL,
rating DECIMAL(3, 2) NULL,
total_pages INTEGER NOT NULL);

CREATE TABLE book_author (
book_author_id SERIAL PRIMARY KEY,
book_id INT NOT NULL,
author_id INT NOT NULL,
CONSTRAINT fk_book FOREIGN KEY(book_id) REFERENCES book(book_id) ON DELETE CASCADE,`
-- fk_book - просто название ограничения
CONSTRAINT fk_author FOREIGN KEY(author_id) REFERENCES author(author_id) ON DELETE CASCADE);
-- ON DELETE CASCADE - удаляет такую строчку в сопряженной таблице

CREATE TABLE orders (
orders_id SERIAL PRIMARY KEY,
status VARCHAR(20) NOT NULL,
total_price DECIMAL(11, 2) NOT NULL,
client_id INTEGER REFERENCES client(client_id) NOT NULL,
CONSTRAINT c1 CHECK (status in ('OPEN', 'IN PROGRESS', 'CLOSED')));`

CREATE TABLE book_order (
book_order_id SERIAL PRIMARY KEY,
book_id INT NOT NULL,
order_id INT NOT NULL,
CONSTRAINT fk_book FOREIGN KEY(book_id) REFERENCES book(book_id) ON DELETE CASCADE,
CONSTRAINT fk_order FOREIGN KEY(order_id) REFERENCES orders(orders_id) ON DELETE CASCADE);

ALTER TABLE client ADD CONSTRAINT sex CHECK (sex in (0,1,2));


