# Basic SSRF Against the Local Server

## Objective  
To exploit the stock check feature by manipulating server-side requests in order to access internal services and perform unauthorized actions.

---

## Observation  
The application’s stock check feature makes server-side requests to retrieve product information from an internal system. The application trusts these internal requests, indicating a potential Server-Side Request Forgery (SSRF) vulnerability.

---

## Exploitation  
I intercepted the request generated when checking product stock using Burp Suite.

I identified that the application was sending a request to an internal URL. I modified this URL to point to internal resources instead of the intended stock endpoint.

This allowed me to redirect the server’s request to the internal admin interface. After gaining access, I was able to perform administrative actions and delete the user Carlos.

---

## Payload Used  
http://localhost/admin  
http://localhost/admin/delete?username=carlos  

---

## Impact  
I was able to perform unauthorized administrative actions by abusing server-side request handling.

An attacker could potentially:
- Access internal-only services (localhost or private network services)  
- Bypass network restrictions  
- Perform administrative actions without authorization  
- Interact with sensitive internal systems not exposed to the public  

---

## Mitigation  
- Do not allow user-controlled input to define server-side request destinations  
- Implement strict allowlists for permitted URLs  
- Block access to internal IP ranges such as 127.0.0.1 and private networks  
- Validate and sanitize all outbound server requests  
- Secure internal admin interfaces with authentication and network segmentation  

---

## Key Learning  
SSRF occurs when a web application allows attackers to control where the server sends requests. If internal systems are trusted without proper validation, attackers can abuse this behavior to access restricted services and perform unauthorized actions.
