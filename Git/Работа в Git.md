- Создание локального репозитория
```bash
git init
выходит предупреждение:
Initialized empty Git repository in /home/kwenus/Documents/test/.git/

посмотреть состояние файлов в отслеживаемой папке:
git status

добавить файлы в отслеживаемые:
git add [имя файла]

добавить все файлы:
git add .

добавить все измененные файлы:
git add -A

сделать коммит:
git commit -m "сообщение"

исправить коммит:
git commit --amend -m "новое сообщение"
```

- Работа историей проекта
```bash
показать историю:
git log --oneline
выведет сообщение:
0a49b8e      (HEAD -> main)   obs_start
хэш-коммита   где находимся   сообщение

git log 
выведет полную информацию по коммиту:
commit 0a49b8e4800e224ca5ac8ff645064cd931403a71 (HEAD -> main)
Author: kwenus <kwenus82@gmail.com>
Date:   Fri Jan 19 18:31:06 2024 +0300
obs_start

git log --all --oneline
выведет полную историю, независимо от того, на каком коммите находится сейчас

переместиться на нужный коммит:
по git log находим хэш нужного коммита, затем
git checkout [хэш коммита]

вернуться к последнему коммиту:
git checkout -
или
git checkout main
```

- Создание удаленного репозитория:
    генерируем ключ (можно оставить все параметры по умолчанию):
```bash
ssh-keygen
```

копируем путь, где хранится ключ, начинается с /.ssh,  
например: /.ssh/id_rsa.pub
далее копируем содержимое ключа
```bash
cat ~/.ssh/id_rsa.pub
```

на сайте **github.com** в разделе **settings** выбираем **SSH and GPG keys**
добавляем туда скопированный ключ и добавляем его (**Add SSH key**)
теперь компьютер связан с сайтом, можно коммитить)

- Работа с удаленным репозиторием:
```bash
проверить есть ли свясь с удаленным репозиторием:
git remote -v

связать локальный репозиторий с удаленным:
git remote add origin [ssh-ссылка(!) на папку удалённого репозитория]
например: git@github.com:kwenus/Obsidian_Vault.git
если https, будет постоянно запрашивать логин и пароль(!)

удалить связь с удаленным репозиторием:
git remote remove origin
```

- Отправка изменений в удаленный репозиторий:
вначале добавить все нужные файлы в индекс, закоммитить, а потом:
```bash
git push -u origin main
```

- Клонирование удаленного репозитория:
```bash
git clone [ssh-ссылка]

что бы сразу указать в какую папку клонировать:
git clone [ssh-ссылка на репозиторий] [имя папки]

забрать все изменения с удаленного репозитория:
git pull
git pull = git fetch + git merge

при командной работе важно всегда вначале забирать изменения с репозитория(!)  
```

- Форк репозитория:
нажимаем кнопку **Fork** на странице нужного репозитория, зетем 
```bash
git clone [ssh-ссылка на репозиторий]
```

- Ветвление:
```bash
показать все ветки проекта
git branch

создать новую ветку:
git branch [имя ветки]

перейти на другую ветку:
git checkout [имя ветки]

создать и сразу переключиться на новую ветку:
git checkout -b [имя ветки]

просмотр истории ветки:
git log [имя-ветки] --graph --oneline

слияние веток:
переключаемся на основную ветку
git checkout main
git merge [имя ветки]

если возникают конфликты, удаляем все лишнее (оставляем только нужный вариант) и технические символы,
добавляем в индекс, коммитим и сливаем ветки.
```

- Отменить коммит:
```bash
git revert [хэш-коммита, который отменить]
попросят разрешить конфдликты, если они есть, зетем
создатся новый коммит, затем отправляем изменения
git push 
```

- .gitignore:
файл в котором указывается то, что не надо отправлять в удаленный репозиторий
```bash
убрать файл из отслеживаемых:
git rm --cached [имя файла]
```
