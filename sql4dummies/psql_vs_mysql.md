## Basic Terminal Navigation: MySQL vs PostgreSQL

This table compares the basic commands for navigating and managing databases in MySQL and PostgreSQL from their respective command-line clients.

| Action                                    | MySQL                                                      | PostgreSQL (psql)              | Notes                                                                    |
| ----------------------------------------- | ---------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------------------ |
| **Connect to server**                     | `mysql -u user -p`                                         | `psql -U user`                 |                                                                          |
| **Connect to specific database**          | `mysql -u user -p database`                                | `psql -U user -d database`     |                                                                          |
| **List databases**                        | `SHOW DATABASES;`                                          | `\l` or `\list`                | MySQL uses SQL; PostgreSQL uses a backslash command.                    |
| **Switch to a database**                  | `USE database_name;`                                       | `\c database_name`             |                                                                          |
| **Show schemas**                          | `SHOW SCHEMAS;` **or** `SHOW DATABASES;` *(they're same)*  | `\dn`                          | In MySQL: *schema = database*. In PostgreSQL: schema = namespace.       |
| **Select a schema**                       | ❌ *(not available)*<br>`USE` only changes **database**    | `SET search_path TO schema;`   | MySQL doesn't distinguish between database and schema.                  |
| **List tables**                           | `SHOW TABLES;`                                             | `\dt schema.*`                 | In PostgreSQL you must specify the schema to filter.                    |
| **List all tables across all schemas**    | —                                                          | `\dt *.*`                      | Includes tables from `public` schema and others.                        |
| **Describe table structure**              | `DESCRIBE table;`<br>`SHOW COLUMNS FROM table;`            | `\d schema.table`              |                                                                          |
| **Describe table in detail**              | —                                                          | `\d+ schema.table`             | Includes size, indexes, storage, etc.                                   |
| **List functions**                        | `SHOW FUNCTION STATUS;`                                    | `\df`                          | MySQL requires a more verbose command.                                  |
| **List views**                            | `SHOW FULL TABLES WHERE Table_type='VIEW';`                | `\dv`                          |                                                                          |
| **List indexes**                          | `SHOW INDEX FROM table;`                                   | `\di schema.table`             | `\di` also supports wildcards.                                          |
| **Execute SQL file**                      | `source file.sql`                                          | `\i file.sql`                  |                                                                          |
| **Show current connection**               | `SELECT DATABASE();`                                       | `\conninfo`                    |                                                                          |
| **Exit client**                           | `exit` or `quit`                                           | `\q`                           |                                                                          |
| **List users (roles)**                    | `SELECT user FROM mysql.user;`                             | `\du`                          | In PostgreSQL these are *roles*, not strictly users.                    |

---

CC BY-NC-SA 4.0 &copy; 2025 | [Antonio L. Martínez Trapote](https://github.com/antoniotrapote)
