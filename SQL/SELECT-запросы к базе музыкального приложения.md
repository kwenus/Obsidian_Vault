- Структура базы:
```sql
create table Genre(
genre_id serial primary key,
title varchar(255) unique
);

create table Musician(
musician_id serial primary key,
musician_name varchar(255) unique
);

create table Album(
album_id serial primary key,
title varchar(255),
release_year int,
constraint release_year check(release_year between 1900 and 2024)
);

create table Track(
track_id serial primary key,
title varchar(255),
duration int not null,
album_id int not null,
constraint fk_album foreign key(album_id) references Album(album_id) on delete cascade
);

create table Compilation(
compilation_id serial primary key,
title varchar(255),
release_year int,
constraint release_year check(release_year between 1900 and 2024)
);

create table compilation_track (
compilation_track_id serial primary key,
compilation_id int not null,
track_id int not null,
constraint fk_compilation foreign key(compilation_id) references Compilation(compilation_id) on delete cascade,
constraint fk_track foreign key(track_id) references Track(track_id) on delete cascade
);

create table genre_musician (
genre_musician_id serial primary key,
genre_id int not null,
musician_id int not null,
constraint fk_genre foreign key(genre_id) references Genre(genre_id) on delete cascade,
constraint fk_musician foreign key(musician_id) references Musician(musician_id) on delete cascade
);

create table musician_album (
musician_album_id serial primary key,
album_id int not null,
musician_id int not null,
constraint fk_album foreign key(album_id) references Album(album_id) on delete cascade,
constraint fk_musician foreign key(musician_id) references Musician(musician_id) on delete cascade
);
```

- Написать SELECT-запросы, которые выведут информацию согласно инструкциям ниже.

	1. Название и продолжительность самого длительного трека.
	2. Название треков, продолжительность которых не менее 3,5 минут.
	3. Названия сборников, вышедших в период с 2018 по 2020 год включительно.
	4. Исполнители, чьё имя состоит из одного слова.
	5. Название треков, которые содержат слово «мой» или «my».

- Написать SELECT-запросы, которые выведут информацию согласно инструкциям ниже.

	1. Количество исполнителей в каждом жанре.
	2. Количество треков, вошедших в альбомы 2019–2020 годов.
	3. Средняя продолжительность треков по каждому альбому.
	4. Все исполнители, которые не выпустили альбомы в 2020 году.
	5. Названия сборников, в которых присутствует конкретный исполнитель (выберите его сами).

- Написать SELECT-запросы, которые выведут информацию согласно инструкциям ниже.

	1. Названия альбомов, в которых присутствуют исполнители более чем одного жанра.
	2. Наименования треков, которые не входят в сборники.
	3. Исполнитель или исполнители, написавшие самый короткий по продолжительности трек, — теоретически таких треков может быть несколько.
	4. Названия альбомов, содержащих наименьшее количество треков.
