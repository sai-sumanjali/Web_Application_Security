# Burp Suite Advanced Techniques

## Intercept and Modify Login Requests

### Step 1: Set Up Burp Suite as Proxy

- Configure your browser to use Burp Suite proxy (default: localhost:8080).
- Enable Intercept in Burp Suite's "Proxy" tab.

### Step 2: Capture Login Request

- Access the login page and input credentials.
- Submit the form.
- Burp will intercept the request.

### Step 3: Modify Request

- In Burp, go to the "Intercept" tab.
- Change parameters as needed (e.g., change username or password).
- Forward the request to test different scenarios.

---

## Perform Fuzzing with Burp Intruder

### Step 1: Send Request to Intruder

- Right-click on the captured request.
- Select "Send to Intruder".

### Step 2: Configure Positions

- In Intruder tab, clear automatic positions.
- Highlight the payload positions (e.g., username or password fields).
- Click "Add" to mark payload positions.

### Step 3: Set Payloads

- In the "Payloads" tab, choose payload types:
  - Names, numbers, or custom lists.
- Input your payload list (e.g., common usernames or passwords).

### Step 4: Start Attack

- Click "Start Attack".
- Analyze responses for successful or interesting results.

---

## Summary

- Intercept login requests to study and modify parameters.
- Use Intruder to automate fuzzing for security testing.
- Always perform these techniques in authorized environments.

---


