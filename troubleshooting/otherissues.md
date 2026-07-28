* **incident id**: 4
* **environment**: wsl(ubuntu)
* **severity**: low
* **issue**:Failure of sqlAlchemy to authenticate my password
---
## Symptom: `RuntimeError: Can't connect to MySQL server on '18@localhost`
## Problem analysis
### sqlAlchemy uses the @ symbol to separete the password from the host my password containing an @ caused it to corrupt the host string srquence
## Fix:```URL-encoded the @ character in your password to %40 (Victor%4018), allowing the driver to parse the URL accurately```

* **incident id**:5
* **environment**:wsl(ubuntu)
* **severity**:
* **issue**:

## Symptom : ` Errno 111 Connection refused followed by Unit mysql.service not found.`
## Pronlem analysis:
 Connection Refused & Missing Linux ServiceThe Challenge: Errno 111 Connection refused followed by Unit mysql.service not found.  The Root Cause: Windows and Linux (WSL) are separate environments. Having MySQL installed on Windows doesn't automatically mean it's running inside Linux. WSL needed its own MySQL daemon installed.  
 ## Fix : How We Fixed It: Installed native MySQL inside Ubuntu
 `(sudo apt install mysql-server)` and booted up the service using sudo service mysql start.  




 