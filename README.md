 PROJECT GUARD-POST: AUTOMATED WEB HEADER HARDENING

 Overview
 
This repository documents Project Guard-Post, a cybersecurity lab project focused on implementing browser-side security controls through
hardened HTTP response headers in Nginx.  

The project was deployed in a containerized environment using Docker on Ubuntu Linux, with validation performed via command-line 
inspection and browser testing.

---

Objectives
- Deploy a standard Nginx web server using Docker.
- Configure browser security headers at the proxy boundary.
- Implement protection against:
  - Clickjacking attacks
  - MIME-type sniffing vulnerabilities
  - Cross-Site Scripting (XSS)
- Validate security controls using HTTP header inspection.

---

 Lab Environment
- Host Platform: VMware Workstation  
- Operating System: Ubuntu Linux  
- Container Platform: Docker  
- Web Server: Nginx  
- Validation Tools: curl, Firefox  

---

Security Controls Implemented
- X-Frame-Options: DENY Mitigates Clickjacking  
- X-Content-Type-Options: nosniff Prevents MIME sniffing  
- Content-Security-Policy: default-src 'self' Restricts unauthorized script execution  

---

 Deployment Steps
1. Installed Docker on Ubuntu Linux.  
2. Pulled the official Nginx Docker image.  
3. Created project directory and configuration files.  
4. Configured hardened `nginx.conf`.  
5. Deployed container and verified accessibility.  
6. Validated headers using `curl -I http://localhost:8080`.

---

 Validation
Example output confirming active security headers:
```bash
HTTP/1.1 200 OK
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Content-Security-Policy: default-src 'self';

