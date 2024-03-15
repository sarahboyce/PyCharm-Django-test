# Test Django project for endpoints and Django Structure

This project is roughly the [Django REST Framework quickstart tutorial](https://www.django-rest-framework.org/tutorial/quickstart/).

Tested on PyCharm 2023.3.4 and this project has no views in Django Structure and no endpoints detected.

These endpoints are expected:

| Endpoint            | View                                   | URL Name              |
|---------------------|----------------------------------------|-----------------------|
| `/`                 | `rest_framework.routers.APIRootView`   | api-root              |
| `/api-auth/login/`  | `django.contrib.auth.views.LoginView`  | rest_framework:login  |
| `/api-auth/logout/` | `django.contrib.auth.views.LogoutView` | rest_framework:logout |
| `/groups/`          | `accounts.views.GroupViewSet`          | group-list            |
| `/groups/<int:pk>/` | `accounts.views.GroupViewSet`          | group-detail          |
| `/users/`           | `accounts.views.UserViewSet`           | user-list             |
| `/users/<int:pk>/`  | `accounts.views.UserViewSet`           | user-detail           |

The user and group ones are defined in the project and I would expect them to be picked up.

## Test Project Set up

Set up for virtual environment
```bash
pip install -r requirements.txt
```
Enable PyCharm Django support.

As I have committed a SQLite database you shouldn't need to migrate.

Run a server
```bash
python manage.py runserver
```
Test the api
```bash
curl -u admin -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/users/
```
It will say: `Enter host password for user 'admin':`
Password is `test12345`

Response:
```
[
    {
        "url": "http://127.0.0.1:8000/users/1/",
        "username": "admin",
        "email": "admin@test.com",
        "groups": []
    }
]
```

You can also see the list of urls by running:
```bash
python manage.py show_urls
```
Which is a `django-extensions` helper function.
