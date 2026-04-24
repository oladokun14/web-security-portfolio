# 2FA Simple Bypass

## Objective  
To bypass the application’s two-factor authentication (2FA) and gain unauthorized access to a user account.

---

## Observation  
The application does not properly enforce the second authentication factor. After entering valid credentials, the user is partially authenticated before completing the 2FA step. This allows access control to be bypassed by manipulating the application flow.

---

## Exploitation  
After obtaining the victim’s username and password, I logged into the application. The application redirected me to the email-based 2FA verification step.

However, instead of completing the 2FA process, I manually modified the URL path in the browser to access a restricted page directly.

---

## Payload Used  
/my-account

---

## Impact  
I gained unauthorized access to a user account without completing the 2FA process.

An attacker could potentially:
- Access sensitive user information  
- Perform actions as a legitimate user  
- Achieve vertical privilege escalation  

---

## Mitigation  
- Ensure full authentication is completed before granting access to protected resources  
- Enforce server-side validation of authentication state  
- Do not rely on client-side routing for security decisions  
- Bind session access strictly to completed 2FA verification  

---

## Key Learning  
This vulnerability occurs when an application incorrectly manages authentication state across multiple steps. If 2FA is not enforced server-side before granting session access, attackers can bypass the security control by manipulating navigation or URLs.
