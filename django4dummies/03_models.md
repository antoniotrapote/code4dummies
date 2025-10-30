
## What is a Model?


## Defining Models
1. **Open `models.py`**: Navigate to the `models.py` file in your app directory (e.g., `myapp/models.py`).
2. **Import necessary modules**: At the top of the file, ensure you have the following import statement:
   ```python
   from django.db import models
   ```
3. **Create a model class**: Define a new class that inherits from `models.Model`. Each attribute of the class represents a database field.
   ```python
   class Person(models.Model):
       first_name = models.CharField(max_length=30)
       last_name = models.CharField(max_length=30)
       birth_date = models.DateField()

       def __str__(self):
           return f"{self.first_name} {self.last_name}"
   ```
**Field types**: Django provides various field types to define the nature of the data. Some common field types include:
   - `CharField`: For short text fields (requires `max_length`).
   - `TextField`: For long text fields.
   - `IntegerField`: For integer values.
   - `DateField`: For date values.
   - `BooleanField`: For true/false values.

## Making Migrations
> Note: Ensure your app is listed in the `INSTALLED_APPS` setting in your project's `settings.py` file. For more details, refer to the [Creating Your First Django App](02_first_app.md) section.

1. **Create migrations**: After defining your models, create migration files that describe the changes to your database schema.
   ```bash
   python manage.py makemigrations app_name
   ```
2. **Apply migrations**: Apply the migrations to update your database schema.
   ```bash
   python manage.py migrate 
   ```  


---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 