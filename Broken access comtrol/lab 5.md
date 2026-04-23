# Broken Access Control - User ID Controlled by Request Parameter with Password Disclosure

## Objective
To identify and exploit a horizontal privilege escalation vulnerability where user account data is exposed via insecure direct object reference (IDOR), leading to sensitive information disclosure.
---

## Observation
The application provides a user account page that displays account details, including the user's password inside a masked input field.

The user account is identified via a request parameter, making it possible to access other users’ account pages by modifying this parameter.

This indicates an IDOR vulnerability combined with sensitive data exposure.

---

## Exploitation
I logged into the application using the provided credentials:

- Username: wiener
- Password: peter

After authentication, I accessed my account page and observed that the page loads user details based on a modifiable user identifier in the request.

I modified this identifier to target the administrator account.

This allowed me to load the administrator’s account page and view the password displayed in the masked input field.

---

## Action Performed
Using the retrieved administrator password, I logged in as the administrator account.

From the admin panel, I performed the required action:

- Deleted the user `carlos`

---

## Impact
This vulnerability allows an attacker to:

- Access other users’ account data via ID manipulation
- Retrieve sensitive credentials (including passwords)
- Perform full account takeover
- Escalate privileges to administrative level
- Completely compromise application integrity

---

## Mitigation
- Do not expose sensitive data (like passwords) in client-side responses
- Enforce strict server-side authorization for all user data access
- Avoid direct object references for user accounts
- Ensure sensitive fields are never sent to the frontend, even in masked form
- Implement proper access control checks for every request

---

## Key Learning
IDOR vulnerabilities become critical when combined with sensitive data exposure. Even if data appears masked, it should never be trusted if delivered to the client.
