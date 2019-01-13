### 1. Устанавка Django

Из корневой папки проекта выполняем
```
$ pipenv install django
```
Эта команда одновременно:
- создаст для этого проекта виртуальное окружение
- установит Django2
- Зафиксирует версии в .lock файле


### 2. Инициализация проекта

```
$ mkdir src && django-admin startproject project src

```

### 3. Добавляем приложение (опционально)

Просто, как пример (через Docker)

```
$ docker-compose run web bash
root@web:/app# cd ./src && python ./manage.py startapp pages
```

### 3. Доступ через браузер

Чтобы запустить локально в режиме отладки (DEBUG) правим `./src/project/settings.py`

```
ALLOWED_HOSTS = ['192.168.99.100', 'localhost', '127.0.0.1']
```
или
```
ALLOWED_HOSTS = ['*']
```

Теперь сайт можно открыть через браузер. На win10 + DockerToolbox `http://192.168.99.100:8000/`


### 5. База данных

В конслоли можно заметить

```
web    | You have 15 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
web    | Run 'python manage.py migrate' to apply them.
```

Меняем конфиг подключения к БД в `./src/project/settings.py`

Ставим библиотеку для работы с PostgeSQL
```
# pipenv install psycopg2
```

Пересобираем контейнер и запускаем миграции

```
$ docker-compose exec web bash
root@web:/app# cd src
root@web:/app/src# ls
db.sqlite3  manage.py  pages  project
root@web:/app/src# python manage.py migrate
```


### 6. Создаем суперпользователя

```
# python manage.py createsuperuser
```

Можно заходить в админку `http://192.168.99.100:8000/admin`
