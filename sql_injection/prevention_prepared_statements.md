# SQL Injection Prevention Using Prepared Statements

Prepared Statements (also known as Parameterized Queries) are one of the most effective ways to prevent SQL Injection attacks. They separate SQL code from data, ensuring that user input is treated strictly as data and never executable code.

---

## What are Prepared Statements?

- SQL queries are predefined with placeholders for user inputs.
- Inputs are bound to placeholders, ensuring proper escaping and datatype handling.
- The database engine compiles the query template once, and then executes it safely with bound parameters.

---

## Example: Preventing SQL Injection in Different Languages

### PHP with MySQLi

### Python with SQLite3

import sqlite3

conn = sqlite3.connect('example.db')
cursor = conn.cursor()

username = input("Username: ")
password = input("Password: ")

# Use ? placeholders for parameters
cursor.execute("SELECT * FROM users WHERE username = ? AND password = ?", (username, password))

rows = cursor.fetchall()

if rows:
    print("Login successful")
else:
    print("Invalid credentials")

conn.close()

---

## Benefits of Using Prepared Statements

- Eliminates SQL Injection risks by treating inputs as data.
- Improved performance for repeated queries.
- Cleaner and more maintainable code.

---

## Additional Prevention Measures

- Validate and sanitize user inputs.
- Use least privilege for database accounts.
- Keep database and libraries up to date.
- Employ Web Application Firewalls (WAF) for additional monitoring.

---


