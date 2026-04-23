# Broken Access Control - Unprotected Admin Functionality (Hidden URL)

## Objective
To identify and access an unprotected admin panel that is hidden at an unpredictable URL, and perform unauthorized administrative actions.

---

## Observation
The application contains an admin panel, but it is not located at a standard path such as `/admin`.

Instead, the admin URL is hidden and only revealed somewhere within the application (e.g. source code, comments, or disclosed resources).

This suggests security through obscurity rather than proper access control.

---

## Exploitation
I reviewed the application and inspected available resources (such as page source and linked files) to locate any references to hidden administrative endpoints.

I discovered the admin panel URL and accessed it directly via the browser.

The panel was accessible without authentication or authorization checks.

---

## Action Performed
Inside the admin interface, I used the available functionality to delete the user:

- carlos

---

## Impact
This vulnerability demonstrates that hiding administrative URLs does not provide security.

An attacker who discovers the hidden path can:
- Access admin functionality
- Modify or delete user accounts
- Fully compromise application integrity

---

## Mitigation
- Do not rely on hidden URLs for security
- Enforce authentication on all admin endpoints
- Implement strict role-based access control (RBAC)
- Validate permissions server-side on every request

---

## Key Learning
Security through obscurity is not a valid security control. Even if admin paths are hidden, they must still be properly protected by authentication and authorization.
