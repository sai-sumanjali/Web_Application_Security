# Cross-Site Scripting (XSS)

## Overview

Cross-Site Scripting (XSS) is a security vulnerability that allows attackers to inject malicious scripts into webpages viewed by other users. XSS attacks can lead to session hijacking, defacement, or redirecting users to malicious sites.

---

## Types of XSS Attacks

### 1. Stored XSS (Persistent)

- Malicious script is permanently stored on the target server, such as in a database or message board.
- Example: Storing a script in a comment field on DVWA (Damn Vulnerable Web Application).
- When other users load the page, the injected script executes in their browsers.

### 2. Reflected XSS

- Malicious code is reflected off a web server, typically via URL query parameters.
- The script is part of the HTTP request and is immediately echoed in the response.
- Example: <script> code in a URL parameter that appears without sanitization on the webpage.

---

## Demonstration

### Stored XSS on DVWA

- Log into DVWA and navigate to the "Stored XSS" challenge.
- Insert a script payload in the input area, e.g., <script>alert('XSS')</script>.
- When the stored input is viewed later, the alert executes, demonstrating XSS.

### Reflected XSS via Query Parameters

- Example vulnerable URL:
- http://vulnerablesite.com/search?q=alert('XSS')

- If the q parameter is not sanitized and reflected in the page, the script runs.

---

## Mitigation Techniques

### 1. Input Validation

- Reject or sanitize all suspicious or unexpected inputs.
- Use whitelisting approaches where possible (allow only expected characters).
- Encode input data before rendering in HTML.

### 2. Content Security Policy (CSP)

- Implement CSP headers to restrict sources of executable scripts.
- Example CSP header:
- Content-Security-Policy: default-src 'self'; script-src 'self' https://trusted.cdn.com

- This helps prevent execution of malicious inline scripts or scripts from untrusted sources.

---


