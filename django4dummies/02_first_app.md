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
    def index(request):
        return HttpResponse("Hello, welcome to my first app!")
    ```

5. **Map the view to a URL**: Create a new file called `urls.py` in your app directory (e.g., `myapp/urls.py`) and map the view to a URL.
    ```python
    from django.urls import path
    from . import views
    urlpatterns = [
        path('', views.index, name='index'),
    ]
    ```

6. **Include the app URLs in the project**: Open the `urls.py` file in your project directory (e.g., `myproject/urls.py`) and include the app's URLs.
    ```python
    from django.contrib import admin
    from django.urls import include, path
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('myapp/', include('myapp.urls')),
    ]
    ```

7. **Run the development server**: Start the development server to test your app.
    ```bash
    python manage.py runserver
    ``` 

8. **Access the app**: Open your web browser and go to `http://127.0.0.1:8000/myapp/` to see your first Django app in action. You should see the message "Hello, welcome to my first app!".

---

## App Structure
```bash
myapp/
├── migrations/      # database migrations for the app
├── __init__.py      # makes this directory a Python package
├── admin.py         # config for Django admin interface
├── apps.py          # app configuration
├── models.py        # database models for the app
├── tests.py         # tests for the app
├── urls.py          # URL declarations for the app
└── views.py         # view functions for the app
```

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote)