- Установка последней версии из репозитория:
```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

- Глобальные настройки 
```bash
git config --global user.name "имя пользователя"
git config --global user.email "эл.почта"

проверка установки:
git config --global --list

задаем правильный формат строк:
git config --global core.autocrlf input
git config --global core.safecrlf warn

убираем нечитаемые строки:
git config --global core.quotepath off

задаем название для основной ветки:
git config --global init.defaultBranch main
```

- Помощь по git:
```bash
общее руководство:
git help -g

помощь по конкретной команде:
git help [команда]
```

- Создание локального репозитория
```bash
git init
выходит предупреждение:
Initialized empty Git repository in /home/kwenus/Documents/test/.git/

посмотреть состояние файлов в отслеживаемой папке:
git status

добавить файлы в отслеживаемые:
git add [имя файла]

```