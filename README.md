# About

Test-Driven Development with Python, Flask, and Docker:

Course (highly recommended): https://testdriven.io/courses/tdd-flask/
Code: https://gitlab.com/testdriven/flask-tdd-docker

My Updates:

1. pin down werkzeug<=0.16.1
2. use flask-restx
3. add some instructions

To start:
```
$ docker-compose up -d --build
$ docker-compose exec users python manage.py recreate_db
$ docker-compose exec users python manage.py seed_db
```

To run tests:

```
$ docker-compose exec users pytest "project/tests"
$ docker-compose exec users pytest "project/tests" -p no:warnings --cov="project"
```

To run flake8, black, and isort:

```
$ docker-compose exec users flake8 project
$ docker-compose exec users black project --check
$ docker-compose exec users /bin/sh -c "isort project/*/*.py --check-only"
```

Then go to:
 - http://127.0.0.1:5001/ping, ping.py
 - http://127.0.0.1:5001/users, list all users
 - http://localhost:5001/admin/user/, flask admin
 - http://127.0.0.1:5001/doc, swagger api docs
