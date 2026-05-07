# Basic SSRF Against the Local Server

## Objective  
To exploit the stock check feature, which fetches data from an internal system, by modifying the request URL to access the admin interface and delete the user Carlos.

---

## Observation  
The application’s stock check feature retrieves data from an internal service hosted on the local server. The server trusts requests originating from itself, which creates an opportunity for Server-Side Request Forgery (SSRF).

---

## Exploitation  
I intercepted the request generated when viewing a product’s stock information and identified the URL used by the server to fetch internal data.

I modified the URL parameter to point to the local admin interface instead of the intended stock resource. This allowed the server to make a request to its own internal admin panel on my behalf.

After gaining access to the admin interface, I used the available functionality to delete the user Carlos.

---

## Payload Used  
Admin interface endpoint and delete user request from the internal admin backend

Example:
```text
http://localhost/admin
http://localhost/admin/delete?username=carlos
