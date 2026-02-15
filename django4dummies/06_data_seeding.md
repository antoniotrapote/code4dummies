# Data seeding
Data seeding is the process of populating a database with initial data. This is particularly useful during development and testing, as it allows developers to work with a consistent set of data without having to manually enter it each time.

### Using data migration
Data migrations allow you to add or modify data as part of a migration process.
1. To create a data migration, you can use the `makemigrations` command with the `--empty` flag. For example, to create an empty migration for the `library` app, you would run the following command:
```bash
python manage.py makemigrations library --empty --name seed_initial_data
```
This will create a new migration file in the `library/migrations` directory. 

2. You can then edit this file to add your data seeding logic. For example:
```python
from django.db import migrations
DATA = [
    {'title': 'The Great Gatsby', 'author': 'F. Scott Fitzgerald'},
    {'title': '1984', 'author': 'George Orwell'},
]

def seed_data(apps, schema_editor):
    Book = apps.get_model('library', 'Book')
    for item in DATA:
        Book.objects.update_or_create(**item)

def unseed_data(apps, schema_editor):
    Book = apps.get_model('library', 'Book')
    Book.objects.filter(title__in=[item['title'] for item in DATA]).delete()

class Migration(migrations.Migration):
    dependencies = [
        ('library', '00xx_previus_migration_file'), # Replace with the actual previous migration file
    ]
    operations = [
        migrations.RunPython(seed_data, unseed_data),
    ]
```

3. Finally, you can apply the migration using the `migrate` command:
```bash
python manage.py migrate
```

4. Check the migration on shell:
```bash
python manage.py shell
from library.models import Book
Book.objects.all()
[<Book: The Great Gatsby>, <Book: 1984>]
```

--------

## Using Django Fixtures
Django provides a built-in way to seed data using fixtures. Fixtures are files that contain serialized data that can be loaded into the database.

### Creating a Fixture
To create a fixture, you can use the `dumpdata` management command. For example, to create a fixture for a model named `Book` in an app named `library`, you would run the following command:
```bash
python manage.py dumpdata library.Book --indent 2 > library/fixtures/books.json
``` 
This command will create a JSON file named `books.json` in the `library/fixtures` directory containing all the data from the `Book` model.

### Loading a Fixture
To load a fixture into the database, you can use the `loaddata` management command. For example, to load the `books.json` fixture you created earlier, you would run the following command:
```bash
python manage.py loaddata library/fixtures/books.json
```
This command will read the data from the `books.json` file and insert it into the database

---
CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote) 