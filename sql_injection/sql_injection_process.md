# SQL Injection Guide

## What is SQL Injection?
SQL Injection (SQLi) is a code injection technique that exploits vulnerabilities in data-driven applications by inserting malicious SQL statements into input fields. Attackers use it to manipulate database queries, leading to unauthorized data access, modification, or destruction.

---

## How to Test for SQL Injection
Testing for SQL Injection involves injecting SQL code into input fields to observe how the application handles it. Common testing methods include:

- *Single Quote Test:* Insert a single quote ' in input fields to check for SQL errors.
- *Boolean-based Test:* Use SQL logical conditions, e.g., ' OR '1'='1 to see if the query always returns true.
- *Error-based Test:* Enter payloads that generate SQL errors to reveal database structure.
- *Union-based Test:* Use UNION SELECT to retrieve data from other database tables.
- *Time-based Test:* Execute commands that delay responses, e.g., '; WAITFOR DELAY '00:00:05';-- to detect blind SQLi.

Example tools for automated testing:
- SQLMap
- Burp Suite
- OWASP ZAP

---

## Best Practices to Prevent SQL Injection
To secure applications against SQLi attacks, follow these best practices:

- Use *Parameterized Queries* or *Prepared Statements* that separate SQL code from data.
- Validate and sanitize all user inputs rigorously.
- Employ ORM (Object-Relational Mapping) tools that abstract direct SQL usage.
- Limit database user privileges to the minimum necessary.
- Avoid displaying detailed database errors to users.
- Use Web Application Firewalls (WAF) to detect and block injection attempts.
- Keep software, frameworks, and libraries updated.

---

## Examples of SQL Injection Payloads and How They Work

| Payload                   | Description                                                  | How It Works                                             |
|---------------------------|--------------------------------------------------------------|----------------------------------------------------------|
| ' OR '1'='1             | Bypasses authentication by making condition always true     | Makes WHERE clause true, returning all rows              |
| ' OR '1'='1' --         | Same as above, with comment to ignore trailing SQL           | Comments out rest of query, bypassing filters            |
| ' UNION SELECT username, password FROM users -- | Steals data from another table                            | Combines attacker’s SELECT with original query           |
| ' ; DROP TABLE users; --| Attempts to delete a database table                          | Executes destructive SQL command post original query     |
| ' WAITFOR DELAY '0:0:5' -- | Time-based blind SQL injection                               | Delays response, confirming vulnerability                |
| "admin' --              | Simple authentication bypass by commenting out password check | Ignores password check causing admin access              |

---

## Summary
SQL Injection attacks remain a severe threat due to their potential to expose or damage critical data. Proper testing, secure coding techniques, and defensive practices are essential to protect applications from SQLi.

---

