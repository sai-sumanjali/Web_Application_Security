# Cross-Site Request Forgery (CSRF) & Token-Based Protection

## CSRF Attack on DVWA to Change Password

A Cross-Site Request Forgery attack tricks an authenticated user into submitting unwanted actions, such as changing passwords, without their consent. Below is an example approach to demonstrate a CSRF attack on DVWA to change a user's password.

### Step 1: Create a Malicious HTML Page for CSRF

- Replace <dvwa_host> with the actual IP or domain.
- When a logged-in victim visits this malicious page, it automatically submits the form, changing their password.

# Demonstrate Token-Based Protection

- DVWA has a CSRF Token mechanism to protect against such attacks. The token is sent along with the form and verified on the server.
- Example of Token Validation in DVWA
- In the form, a token field is present:<input type="hidden" name="csrf_token" value="random_token_value">

### The server validates this token before executing the password change:
- If the token is valid and matches the server's stored token, the request proceeds.
- If the token is missing or mismatched, the server rejects the request.

###How Token-Based Protection Works
- Server generates a unique token for each form/session.
- Token is embedded as a hidden field in the form.
- On submission, server verifies the token, ensuring the request originates from the genuine form.

#Summary
- To demonstrate CSRF without protection, create a malicious form that submits a password change request.
- To prevent CSRF, always implement token-based validation which ensures requests are legitimate.
- Always test CSRF protections in controlled environments only.

---


