# Admin superuser
In Django, a superuser is a special type of user that has all permissions and can manage the entire site through the admin interface. Creating a superuser is essential for accessing the Django admin panel and performing administrative tasks.

## Creating a Superuser
To create a superuser, follow these steps:
1. **Open your terminal**: Navigate to your Django project directory where the `manage.py` file is located.
   ```bash
   cd path/to/your/project
   ```
2. **Run the createsuperuser command**: Execute the following command to start the superuser creation process.
   ```bash
   python manage.py createsuperuser
   ```
3. **Provide user details**: You will be prompted to enter a username, email address, and password for the superuser. Follow the prompts to complete the process.
   ```bash
   Username (leave blank to use 'your-username'): admin
   Email address: (optional)
   Password: ********
   Password (again): ********
   ```
    Expect to see a confirmation message like this:
    ```
    >>> Superuser created successfully.
    ```

## Registering Models in the Admin Interface
To manage your models through the Django admin interface, you need to register them in the `admin.py` file of your app. Here’s how to do it:
1. **Open `admin.py`**: Navigate to the `admin.py` file in your app directory (e.g., `myapp/admin.py`).
2. **Import your models**: At the top of the file, import the models you want to register.
   ```python
   from django.contrib import admin
   from .models import YourModel
   ```
3. **Register the models**: Use the `admin.site.register()` function to register your models.
   ```python
   admin.site.register(YourModel)
   ```

## Accessing the Admin Interface
1. **Start the development server**: If your server is not already running, start it with the following command:
   ```bash
   python manage.py runserver
   ```
2. **Open your web browser**: Navigate to the admin interface by going to `http://127.0.0.1:8000/admin/`.

3. **Log in**: Use the superuser credentials you created earlier to log in to

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 