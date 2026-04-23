# Path Traversal - Lab 01

## Objective
To understand how path traversal vulnerabilities allow access to restricted files outside the intended directory.

---

## Observation
The application retrieves files based on user-controlled input. The input is not properly validated or restricted, suggesting that directory traversal may be possible.

---

## Exploitation
I intercepted the request and modified the file parameter to manipulate the file path. By injecting traversal sequences, I was able to access files outside the intended directory structure.

---

## Payload Used  
../../../../etc/passwd



---

## Impact
The application exposed sensitive system file content.  

An attacker could potentially:
- Access sensitive configuration files
- Read system-level data
- Identify users and system structure
- Escalate further attacks based on exposed information

---

## Mitigation
- Validate and sanitize all file input
- Restrict file access to a predefined directory (whitelisting approach)
- Avoid direct user control over file system paths
- Implement secure file handling mechanisms on the server side

---

## Key Learning
Path traversal occurs when user input is directly used in file operations without proper validation. Even small input manipulation can lead to significant information disclosure.
