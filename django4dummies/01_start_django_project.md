## 🚀 Start a Django project

To create an app with Django, follow these steps:
1. **Navigate to your project directory**: Open your terminal and move to the folder where you want to create your project.

   ```bash
   cd path/to/your/project
   ```

2. **Create a virtual environment**: It’s good practice to isolate project dependencies.

   ```bash
   python -m venv env
   ```
3. **Activate the virtual environment**:
   - On Windows:
     ```bash
     .\env\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source env/bin/activate
     ```        

4. **Install Django**: Use pip to install Django in your virtual environment.
    ```bash
    pip install django
    ```

5. **Create the project**: Use the `django-admin startproject` command followed by your project name.

   ```bash
   django-admin startproject myproject .
   ```

- `.` at the end specifies that the project should be created in the current directory.

6. **Create de database migrations**: Run the following command to create the necessary database tables.

   ```bash
   python manage.py migrate
   ```

7. **Preview the project**: Start the development server to preview your project in a web browser.

   ```bash
   python manage.py runserver
   ```

8. **Access the project**: Open your web browser and go to `http://127.0.0.1:8000/` to see your Django project in action.

---

## 📁 Project Structure
```bash
myproject/
├── manage.py.        # main script to manage the project
├── myproject/.       # project configuration directory
│   ├── __init__.py   # makes this directory a Python package
│   ├── settings.py   # project settings  
│   ├── urls.py       # URL declarations
│   ├── asgi.py       
│   └── wsgi.py
├── db.sqlite3       # SQLite database file
```
