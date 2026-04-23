# Broken Access Control - User Role Controlled by Request Parameter (Cookie-Based)

## Objective
To identify and exploit insecure role management where user privileges are determined by a modifiable request parameter (cookie), and use this to access admin functionality.

---

## Observation
The application contains an admin panel at `/admin`.

Access to this panel is restricted based on user role, which is determined using a cookie value.

Since cookies are controlled on the client side, they may be susceptible to manipulation.

---

## Exploitation
I logged into the application using the provided credentials:

- Username: wiener
- Password: peter

After authentication, I inspected the session cookies and identified a parameter controlling user role.

I modified the cookie value to elevate privileges to an administrator role and then accessed the `/admin` panel.

---

## Action Performed
After gaining admin access, I used the available functionality to delete the user:

- carlos

---

## Impact
This vulnerability allows an attacker to:

- Escalate privileges by modifying client-side data
- Access restricted administrative functionality
- Modify or delete user accounts
- Fully compromise application integrity

---

## Mitigation
- Do not trust client-side data (cookies, parameters) for authorization
- Store user roles securely on the server side
- Validate session permissions on every request
- Use signed and tamper-proof session tokens

---

## Key Learning
Authorization must never depend on client-controlled data. Cookies can be manipulated unless properly signed and validated on the server.
