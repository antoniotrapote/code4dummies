# Setup postgreSQL database for Django project
This guide will help you set up a PostgreSQL database for your Django project.

## Step 1: Install PostgreSQL
First, ensure that PostgreSQL is installed on your system. You can download it from the [official PostgreSQL website](https://www.postgresql.org/download/) or use a package manager.

## Step 2: Install psycopg2
Django requires the `psycopg2` package to interact with PostgreSQL. You can install it using pip:
```bash
pip install psycopg2-binary
``` 

## Step 3: Create a PostgreSQL Database and User
1. Open your terminal and access the PostgreSQL prompt:
   ```bash
   psql postgres
   ```
2. Create a new database for your Django project:
   ```sql
   CREATE DATABASE your_database_name;
   ```
3. Create a new user and set a password:
   ```sql
   CREATE USER your_username WITH PASSWORD 'your_password';
   ```
4. Grant all privileges on the database to the user:
   ```sql
   GRANT ALL PRIVILEGES ON DATABASE your_database_name TO your_username;
   ```
5. Exit the PostgreSQL prompt:
   ```sql
   \q
   ```  

## Step 4: Configure Django to Use PostgreSQL
1. Open your Django project's `settings.py` file.
2. Locate the `DATABASES` section and update it to use PostgreSQL:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_database_name',
        'USER': 'your_username',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',  # Set to empty string for localhost.
        'PORT': '5432',       # Default PostgreSQL port.
    }
}
```

## Step 5: Migrate the Database
Run the following command to apply migrations and create the necessary database tables:
```bash
python manage.py migrate
``` 
## Step 6: Test the Connection
Start the Django development server to ensure everything is set up correctly:
```bash
python manage.py runserver
```
If the server starts without errors, your PostgreSQL database is successfully set up for your Django project.

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 