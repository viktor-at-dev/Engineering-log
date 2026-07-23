* **incident id**: 4
* **environment**: wsl(ubuntu)
* **severity**: low
* **issue**:Failure of sqlAlchemy to authenticate my password
---
## Symptom: `RuntimeError: Can't connect to MySQL server on '18@localhost`
## Problem analysis
### sqlAlchemy uses the @ symbol to separete the password from the host my password containing an @ caused it to corrupt the host string srquence
## Fix:```URL-encoded the @ character in your password to %40 (Victor%4018), allowing the driver to parse the URL accurately```




 