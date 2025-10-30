# Creating Your First Django App
In this section, we will create your first Django app within the project you set up earlier. An app in Django is a web application that does something, such as a blog system, a database of public records, or a simple poll application.

## 🛠️ Create a Django Ap
To create a Django app, follow these steps:
1. **Navigate to your project directory**: Open your terminal and move to the folder where your Django project is located.
    ```bash
    cd path/to/your/project
    ```
2. **Create the app**: Use the `python manage.py startapp` command followed by your app name. For this example, we will create an app called `myapp`.
    ```bash
    python manage.py startapp myapp
    ``` 
3. **Register the app**: Open the `settings.py` file located in your project directory (e.g., `myproject/settings.py`) and add your new app to the `INSTALLED_APPS` list.
    ```python
    INSTALLED_APPS = [
        ...
        'myapp',
    ]
    ```
4. **Create a view**: Open the `views.py` file in your app directory (e.g., `myapp/views.py`) and create a simple view function.
    ```python
    from django.http import HttpResponse


---

## App Structure
```bash
myapp/
├── migrations/      # database migrations for the app
├── __init__.py      # makes this directory a Python package
├── admin.py         # config for Django admin interface
├── apps.py          # app configuration
├── models.py        # database models for the app
├── tests.py         # tests for the app
└── views.py         # view functions for the app
```

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 