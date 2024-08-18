# Django-Todolist

Django-Todolist is a todolist web application with the most basic features of most web apps, i.e. accounts/login, API and (somewhat) interactive UI.

---
CSS | [Skeleton](http://getskeleton.com/)
JS  | [jQuery](https://jquery.com/)

## Explore
Try it out by installing the requirements. (Works only with python >= 3.8, due to Django 4)

    pip install -r requirements.txt

Create a database schema:

    python manage.py migrate

And then start the server (default: http://localhost:8000)

    python manage.py runserver


Now you can browse the [API](http://localhost:8000/api/)
or start on the [landing page](http://localhost:8000/)

## Task
#### Prerequisites
- Fork this repository
- Open requirements.txt
- Add mysql-connector-python==8.2.0
- Open file todolist/settings.py
- Go to line DATABASES on line 64
- Update it with this code:

    ```
    DATABASES = {
        'default': {
            'ENGINE': 'mysql.connector.django',
            'NAME': 'app_db',
            'USER': 'app_user',
            'PASSWORD': '1234',
            'HOST': 'localhost',  # You can use a different host in your MySQL server is on a remote machine.
            'PORT': '',  # Leave this empty to use the default MySQL port (3306).
        }
    }

    ```
#### Requirements
1. Prepare a Dockerfile to run a MySQL database, based on official MySQL Image, name file Dockerfile.mysql
2. Dockerfile should contain ENV variables to initialize app_db database
3. Dockerfile should contain ENV variables to initialize app_user with password 1234
4. Build mysql image with a name and tag mysql-local:1.0.0
5. You should be able successfully run a container with MySQL with a Volumes Attached
6. Push mysql-local:1.0.0 to your personal docker hub into mysql-local repository
7. Run mysql-local:1.0.0 onn your machine
8. Update the python app db config with an IP of a running MySQL server container (without it, the app container won’t build)
9. Build and run your updated app
10. Take a screenshot of a terminal with successfully started application
11. Push Image with a name and tag: todoapp:2.0.0 to yout Docker Hub repository
12. Update README.md with instructions on how to run MySQL container with a volume attached
13. Update README.md with instructions on how to run an App container which will connect to a MySQL db container.
14. README.md should contain a link to your personal docker hub repository win an app image
15. README.md should contain instructions on how to access the application via a browser.
16. Create PR with your changes and attach it for validation on a platform


[//]: # (Update README.md with instructions on how to run MySQL container with a volume attached)

## How to run MySQL container with a volume attached

To run MySQL container with a volume attached, you can use the following commands:

```bash
docker pull andr1yk/mysql-local:1.0.0
docker run -d -v mysql-data:/var/lib/mysql --name app-db -p 3306:3306 andr1yk/mysql-local:1.0.0
```

[//]: # (Update README.md with instructions on how to run an App container which will connect to a MySQL db container.)

## How to run an App container

To run an App container which will connect to a MySQL db container, you can use the following commands:

```bash
docker pull andr1yk/devops-todoapp:2.0.0
docker run -d -p 8080:8080 --name app andr1yk/devops-todoapp:2.0.0
```

[//]: # (README.md should contain a link to your personal docker hub repository win an app image)

## Personal Docker Hub repository

Mysql image: [andr1yk/mysql-local](https://hub.docker.com/r/andr1yk/mysql-local)

App image: [andr1yk/devops-todoapp](https://hub.docker.com/r/andr1yk/devops-todoapp)

[//]: # (README.md should contain instructions on how to access the application via a browser.)

## How to access the application via a browser

To access the application via a browser, you can use the following link:

[http://localhost:8080/](http://localhost:8080/)
