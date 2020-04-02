# About

Authentication with Flask, React, and Docker:

- Course (highly recommended): https://testdriven.io/courses/auth-flask-react/getting-started/
- Code: https://gitlab.com/testdriven/flask-react-auth

My Updates:

1. pin down werkzeug<=0.16.1
2. use flask-restx
3. add some instructions

## Run

To run:

http://localhost:3007

```
$ export REACT_APP_USERS_SERVICE_URL=http://localhost:5001
$ docker-compose up -d --build
$ docker-compose exec users python manage.py recreate_db
$ docker-compose exec users python manage.py seed_db
$ docker-compose stop
```
then go to http://localhost:3007

backend tests:

```
$ docker-compose exec users python -m pytest "project/tests" -p no:warnings
$ docker-compose exec users flake8 project
$ docker-compose exec users black project
$ docker-compose exec users /bin/sh -c "isort project/**/*.py"
```

frontend tests:

```
$ docker-compose exec client npm test
$ docker-compose exec client npm run prettier:check
$ docker-compose exec client npm run lint
```

Other commands:

```
$ docker-compose down
$ docker-compose down -v
```

## Other Notes

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


 React: http://localhost:3000

 ```
 $ node -v
 $ npm -v
 $ npm install create-react-app --global
 $ npm start
 $ npm install axios
 $ export REACT_APP_USERS_SERVICE_URL=http://localhost:5001
 $ npm install --save-dev @testing-library/react
 $ npm test # in serivces/client folder
 $ ./node_modules/.bin/react-scripts test --coverage
 $ npm install prop-types
 ```

 React docker: http://localhost:3007

 ```
 $ export REACT_APP_USERS_SERVICE_URL=http://localhost:5001
 $ docker-compose up -d --build
 $ docker-compose exec users python manage.py recreate_db
 $ docker-compose exec users python manage.py seed_db
 $ docker-compose exec client npm test
 ```

 ssh to container

 ```
 $ docker-compose exec users /bin/sh
 $ docker-compose exec users-db /bin/sh
 ```


Docker:
```
$ docker system prune -a --volumes # delete everything
```

Auto reloading not working solution:

I deleted virtual box, remove everything with `$ docker system prune -a --volumes`, deleted docker, restart the Mac (Catalina), get the latest Docker for Mac Desktop, then it works.

linting and formatting:

```
$ docker-compose exec client npm run prettier:check
$ docker-compose exec client npm run lint
```
