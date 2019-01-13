# How to start

1. From root directory
```
$ docker-compose up
```

2. Apply migrations
```
$ docker-compose exec web bash
# cd src
# python manage.py migrate
```

3. Create superuser
```
# python manage.py createsuperuser
```

Now you can login into web-backend at http://192.168.99.100:8000/admin (Docker Toolbox on Win)
