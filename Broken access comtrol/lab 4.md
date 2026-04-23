# Broken Access Control - User ID Controlled by Request Parameter (GUID-based IDOR)

## Objective
To identify and exploit a horizontal privilege escalation vulnerability where user accounts are identified using GUIDs, allowing unauthorized access to another user's sensitive data.

---

## Observation
The application uses GUIDs (Globally Unique Identifiers) instead of sequential IDs to identify user accounts on the profile page.

Although the IDs are not easily guessable, they are still exposed within the application responses.

This indicates a potential Insecure Direct Object Reference (IDOR) vulnerability.

---

## Exploitation
I logged into the application using the provided credentials:

- Username: wiener
- Password: peter

After authentication, I accessed my account page and inspected the request/response data to identify how user accounts are referenced.

I then searched within the application responses to locate the GUID associated with the user `carlos`.

Once identified, I used the GUID to directly access Carlos’s account information.

---

## Action Performed
From Carlos’s account page, I retrieved his API key.

This API key was submitted as the solution to complete the lab.

---

## Impact
This vulnerability allows an attacker to:

- Access other users’ accounts using exposed identifiers
- Retrieve sensitive information (e.g. API keys)
- Perform horizontal privilege escalation
- Compromise user data confidentiality

---

## Mitigation
- Do not expose direct object references (IDs or GUIDs) in responses
- Enforce server-side authorization checks on every request
- Ensure users can only access their own data
- Use indirect reference mapping instead of raw identifiers

---

## Key Learning
Even non-sequential identifiers like GUIDs do not provide security. If access control is not enforced on the server side, attackers can still exploit exposed references.
