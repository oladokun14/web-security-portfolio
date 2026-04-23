# Broken Access Control - Unprotected Admin Functionality

## Objective
To identify and exploit an unprotected admin panel that allows unauthorized users to perform administrative actions.

---

## Observation
The application exposes an admin panel at `/admin` that is not protected by authentication or authorization mechanisms.

This indicates that sensitive functionality may be accessible without verifying user roles.

---

## Exploitation
I navigated directly to the `/admin` endpoint without any authentication requirements.

The admin interface was accessible, confirming missing access control protections.

---

## Action Performed
Within the admin panel, I identified user management functionality and proceeded to delete the target user:

- carlos

---

## Impact
This vulnerability allows any user to:
- Access administrative functionality
- Modify or delete user accounts
- Fully compromise application integrity

This represents a critical access control failure.

---

## Mitigation
- Protect all admin endpoints with strict authentication
- Implement server-side role-based access control (RBAC)
- Ensure sensitive routes are not publicly accessible
- Do not rely on hidden URLs for security

---

## Key Learning
Administrative functionality must always be protected by proper authorization checks. Exposure of admin interfaces leads to full application compromise.
