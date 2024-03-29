
Для того? чтобы **поменять редактор по умолчанию** для пользователя воспользуемся следующей командой:

```bash
update-alternatives --config editor
```

[![Как изменить текстовый редактор по умолчанию Ubuntu](https://blog.sedicomm.com/wp-content/uploads/2017/05/izobrazhenie_2021-02-19_223151.png)](https://blog.sedicomm.com/wp-content/uploads/2017/05/izobrazhenie_2021-02-19_223151.png)  

## Как изменить текстовый редактор по умолчанию в Ubuntu для пользователя root

Если необходимо **изменить редактор** в **Ubuntu** для пользователя **root**, то необходимо ввести команду с **sudo**:

```bash
sudo update-alternatives --config editor
```
Мы видим, что по умолчанию стоит редактор **nano**. Нажимаем **4**, чтобы редактором по умолчанию был **vim**. Далее необходимо перелогиниться, чтобы изменения вступили в силу.