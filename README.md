📌 Project Overview

This project demonstrates the setup and testing of SafeLine Web Application Firewall (WAF) with Damn Vulnerable Web Application (DVWA) in a controlled cybersecurity lab environment.

The main purpose of this project is to understand how a Web Application Firewall detects, monitors, and blocks common web attacks.

🎯 Objectives

- Set up SafeLine WAF in a virtual lab environment.
- Deploy DVWA as a vulnerable web application.
- Configure SafeLine as a reverse proxy/WAF for DVWA.
- Configure authentication and access-control features.
- Test SQL Injection protection.
- Test HTTP flood/basic access protection.
- Configure custom deny rules.
- Monitor and analyze blocked security events.

🏗️ Lab Architecture

                 ┌─────────────────┐
                 │   Kali Linux    │
                 │  Security Tests │
                 └────────┬────────┘
                          │
                          │ HTTPS
                          ▼
                 ┌─────────────────┐
                 │   SafeLine WAF  │
                 │   Reverse Proxy │
                 │   Security      │
                 └────────┬────────┘
                          │
                          │ HTTP
                          ▼
                 ┌─────────────────┐
                 │ Ubuntu Server   │
                 │ Apache + DVWA   │
                 └─────────────────┘

🖥️ Technologies Used

- Ubuntu Server
- Kali Linux
- VirtualBox
- SafeLine WAF 9.4.0
- Docker
- Apache2
- DVWA
- MySQL/MariaDB
- Nginx
- cURL
- ApacheBench
- Nmap
- Burp Suite

⚙️ Project Setup

1. Ubuntu Server

Ubuntu Server was used to host the vulnerable web application and SafeLine WAF.

DVWA was deployed under:

/var/www/html/DVWA

Apache was configured to serve DVWA on port:

8080

2. SafeLine WAF

SafeLine WAF was installed using Docker.

The SafeLine management interface was configured to run on:

https://localhost:9443

SafeLine was configured as a reverse proxy in front of DVWA.

3. DVWA Backend

The DVWA backend was accessible through:

http://<UBUNTU-IP>:8080/DVWA/

The public application was accessed through the SafeLine-protected domain:

https://www.dvwa.local/DVWA/

🔐 SafeLine Security Configurations

The following security features were configured and tested:

SQL Injection Protection

SafeLine was configured to detect SQL Injection attempts.

A test SQL Injection payload was used against the DVWA application in the controlled lab environment.

Example:

1' OR '1'='1

The malicious request was detected and blocked by SafeLine.

HTTP Flood / Access Protection

Basic access-limit protection was configured to demonstrate protection against excessive HTTP requests.

Testing was performed using ApacheBench.

Example:

ab -n 20 -c 5 https://www.dvwa.local/DVWA/

Authentication

SafeLine Auth Sign-In was configured using account-password authentication.

This adds an authentication layer before users can access the protected application.

Custom Deny Rule

A custom deny rule was configured to demonstrate IP-based access control.

The rule was tested from the Kali Linux testing environment.

🧪 Security Testing

Testing was performed from Kali Linux against the SafeLine-protected DVWA application.

Test 1 — Normal Request

A normal request was sent to the application.

Expected result:
Request is allowed and DVWA is accessible.

Test 2 — SQL Injection

A SQL Injection test was performed against DVWA.

Expected result:
SafeLine detects the malicious request and blocks it.

Test 3 — HTTP Flood

Multiple HTTP requests were generated using ApacheBench.

Expected result:
SafeLine's access protection can detect excessive requests according to the configured limits.

Test 4 — Custom Deny Rule

The configured deny rule was tested from Kali Linux.

Expected result:
Requests matching the configured rule are denied.

📊 Results

Security Test| Result
Normal DVWA request| ✅ Allowed
SQL Injection| 🛡️ Blocked by SafeLine
HTTP Flood testing| 🛡️ Protection configured
Custom deny rule| 🛡️ Blocked matching requests
Authentication| 🔐 Configured
Security event monitoring| ✅ Verified

📸 Screenshots

Screenshots demonstrating the project can be added to the "screenshots" folder.

Recommended screenshots:

1. SafeLine dashboard
2. SafeLine application configuration
3. DVWA login page
4. SafeLine authentication page
5. SQL Injection blocked message
6. SafeLine security event/log
7. HTTP flood testing
8. Custom deny rule
9. Docker containers running
10. Apache/DVWA working

Example:

![SafeLine Dashboard](screenshots/safeline-dashboard.png)

🔒 Ethical Use

DVWA is intentionally vulnerable and this project was performed in an isolated, controlled lab environment.

The techniques demonstrated in this repository should only be used on systems that you own or have explicit permission to test.

📚 Learning Outcomes

Through this project, I learned:

- Basic WAF concepts
- Reverse proxy configuration
- Docker-based security infrastructure
- Web application security
- SQL Injection detection
- HTTP flood protection
- Authentication controls
- IP-based access control
- Security event monitoring
- Vulnerability testing in a controlled environment

🚀 Future Improvements

Possible future improvements include:

- Adding more WAF security rules
- Testing additional DVWA vulnerabilities
- Improving monitoring and logging
- Adding automated security testing
- Integrating additional security tools
- Improving network isolation and lab documentation

👩‍💻 Author

Shravni Ambhore 

BSc Cyber & Digital Science Student
