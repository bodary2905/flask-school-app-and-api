# School App and API - демо приложение для тренировки написания автотестов

This is a Flask app with an API layer. It has the following properties:

1. It has the following relational entities:
    1. Student
    2. Teacher
    3. Subject
2. Each student can have only one subject as a major, but can read any subject as well (minors)
3. A subject is taught by one teacher
4. It has endpoints to CREATE, UPDATE, and DELETE each entity in the application
5. Only an authorized user can access the endpoints

## Installation and Set Up

Clone the repo from GitHub:

```
https://github.com/bodary2905/flask-school-app-and-api.git
```

Install the required packages:

```
poetry install
```

Установить Postgres по [инструкции](https://winitpro.ru/index.php/2019/10/25/ustanovka-nastrojka-postgresql-v-windows/).
Запомнить имя пользователя (`user`), пароль (`password`) и создать базу данных `database_name` - эти данные понадобятся
на следующем шаге

Create a `.env` file with the following keys:

```
SECRET_KEY=school # любое ваше слово - используется для шифрования паролей
DATABASE_URI=postgresql+psycopg2://user:password@hostname/database_name # поменять user, password, hostname, database_name
TEST_DATABASE_URI=- # это БД для unit-тестов - для нас не интересно
ENVIRONMENT=development #  или production - на что влияет - не разбиралась 
```

Initialize, migrate, and upgrade the database:

```
python manage.py db init
python manage.py db migrate
python manage.py db upgrade
```

## Launching the Program

Run ```python run.py```. You may
use [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop?hl=en) for Google
Chrome to run the API.

## API Endpoints

| Resource URL                   | Methods          | Description                             | Requires Token |
|--------------------------------|------------------|-----------------------------------------|----------------|
| `/api/v1`                      | GET              | The index                               | FALSE          |
| `/api/v1/auth/register`        | POST             | User registration                       | FALSE          |
| `/api/v1/auth/login`           | POST             | User login                              | FALSE          |
| `/api/v1/students`             | GET, POST        | View all students, add a student        | TRUE           |
| `/api/v1/students/<string:id>` | GET, PUT, DELETE | View, edit, and delete a single student | TRUE           |
| `/api/v1/teachers`             | GET, POST        | View all teachers, add a teacher        | TRUE           |
| `/api/v1/teachers/<string:id>` | GET, PUT, DELETE | View, edit, and delete a single teacher | TRUE           |
| `/api/v1/subjects`             | GET, POST        | View all subjects, add a subject        | TRUE           |
| `/api/v1/subjects/<string:id>` | GET, PUT, DELETE | View, edit, and delete a single subject | TRUE           |

## Sample API Requests

Registering and logging in to get a JWT token:
![User Registration](screenshots/api_register.png)

![User Login](screenshots/api_login.png)

Displaying a paginated list of teachers:
![List of Teachers](screenshots/api_list_teachers.png)

Displaying a paginated list of subjects:
![List of Subjects](screenshots/api_list_subjects.png)

Updating a student:
![Updating Student](screenshots/api_update_student.png)

Login:
![User Login](screenshots/app_login.png)

Dashboard:
![App Dashboard](screenshots/app_dashboard.png)

Displaying all students:
![Students](screenshots/app_students.png)

Displaying all teachers:
![Teachers](screenshots/app_teachers.png)

Displaying all subjects:
![Subjects](screenshots/app_subjects.png)

## Credits

Copyright (c) 2018 [Mbithe Nzomo](https://github.com/mbithenzomo)
