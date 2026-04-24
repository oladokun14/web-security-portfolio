
# Username Enumeration via Different Responses and Password Brute Force Attack

## Objective  
To identify a valid username through response differences in the login process and exploit weak password security using a brute force attack.

---

## Observation  
The application behaves differently depending on whether a username is valid or invalid during login attempts. This response discrepancy allows username enumeration. Additionally, weak or predictable passwords increase the risk of successful brute force attacks.

---

## Exploitation  
On the login page, I entered a random username and password, intercepted the request using Burp Suite, and sent it to Intruder.

Using a simple wordlist provided by PortSwigger Web Security Academy, I tested multiple usernames and observed differences in the server’s response to identify a valid username.

After confirming the correct username, I performed a password brute force attack using the same method until I found the correct password and successfully logged into the account.

---

## Payload Used  
Simple username and password wordlist provided by PortSwigger

---

## Impact  
I gained unauthorized access to a user account.

An attacker could potentially:
- Access sensitive user information  
- Perform actions as the legitimate user  
- Escalate attacks using compromised account access  
- Exploit weak authentication mechanisms further

---

## Mitigation  
- Ensure login responses are consistent for both valid and invalid usernames  
- Prevent username enumeration by avoiding distinguishable error messages  
- Enforce strong password policies  
- Implement account lockout or rate limiting after multiple failed attempts  
- Use multi-factor authentication (MFA) where possible

---

## Key Learning  
Username enumeration occurs when an application reveals whether a username is valid through differences in login responses. Combined with weak passwords, this can lead to successful brute force attacks and unauthorized access.
