---
share: true
---
To analyze .pcapng file
```
1. Look at bytes in request and try to target improtant informations like /etc/passwd for example

2. Then right click on the selected request and press follow TCP to display informations

```

# Apply Filter to see something 

To analyze large amounts of data, it is sometimes helpful to filter the data.

For example: I have encountered several challenges in which I had to find a username and password in a Wireshark file.

The first step is to filter:

If we're looking for an SSH connection, we can start by filtering for POST requests (since the user sends their password to the server). 

```
http.request.method == "POST"
```

Then we can filter with code : 200 request :

```
2337	43.880318347	192.168.111.136	192.168.111.136	HTTP	774	HTTP/1.1 200 OK  (text/html)
```

If you follow TCP you will find : 

```
"uname=valleyDev&psw=ph0t0s1234&remember=on"
```
