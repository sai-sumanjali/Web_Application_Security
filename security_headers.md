# Web Security Headers

## Analyze Security Headers with SecurityHeaders.com

1. Go to [https://securityheaders.com](https://securityheaders.com).
2. Enter the URL of your target or test site.
3. Review the report showing the HTTP security headers implemented and their grades.
4. Identify missing or weak headers to improve.

---

## Important HTTP Security Headers to Add

- *Content-Security-Policy (CSP):* Controls sources for scripts, styles, etc. Helps prevent XSS attacks.
- *Strict-Transport-Security (HSTS):* Enforces HTTPS connections.
- *X-Frame-Options:* Prevents clickjacking by restricting iframe embedding.
- *X-Content-Type-Options:* Stops MIME-type sniffing.
- *Referrer-Policy:* Controls referrer information sent with requests.
- *Permissions-Policy:* Restricts browser features and APIs.

---

## Adding Security Headers in Apache Configuration

Edit your Apache site's configuration file (e.g., /etc/apache2/sites-available/000-default.conf) or .htaccess:

# Enable headers module
##a2enmod headers

# Mitigate Clickjacking
Header set X-Frame-Options "SAMEORIGIN"

# Referrer Policy
Header set Referrer-Policy "no-referrer-when-downgrade"

# Content Security Policy example (adjust as needed)
Header set Content-Security-Policy "default-src 'self'; script-src 'self' https://trusted.cdn.com; object-src 'none';"

# HTTP Strict Transport Security (HSTS)
Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"

# Permissions Policy (formerly Feature Policy)
Header set Permissions-Policy "geolocation=(), microphone=()"

# After Adding Headers
### 1. Restart Apache to apply changes:

sudo systemctl restart apache2

### 2. Re-test your site to verify headers.

securityheaders.com

# Summary
- Proper HTTP security headers add essential layers of defense to protect web applications from common attacks. Regular analysis and configuration updates are recommended.

---



