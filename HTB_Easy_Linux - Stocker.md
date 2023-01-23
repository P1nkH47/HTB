![image](https://user-images.githubusercontent.com/51139868/214156666-1b51c4b8-8e16-4095-b2f9-e2f5eefe306a.png)

First of all I ran an nmap scan which gave me the following output:

``` bash
➜  ~ sudo nmap -sC -sV -Pn 10.10.11.196
[sudo] password for kali: 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-01-23 16:41 EST
Nmap scan report for 10.10.11.196
Host is up (0.15s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 3d12971d86bc161683608f4f06e6d54e (RSA)
|   256 7c4d1a7868ce1200df491037f9ad174f (ECDSA)
|_  256 dd978050a5bacd7d55e827ed28fdaa3b (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://stocker.htb
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.99 seconds
```
I tried pasting the IP address directly on the search bar but I had to add it to my /etc/hosts before I could access the interface.

![image](https://user-images.githubusercontent.com/51139868/214157207-165169f6-f18a-4d4d-a7e9-aa6ed2097e1f.png)

It opens a very pretty web application

![image](https://user-images.githubusercontent.com/51139868/214157563-6ff4165d-a260-4d45-b7a7-f6b891aaebda.png)

As usual, I checked the source-code for information but nothing interesting seemed to be there.

![image](https://user-images.githubusercontent.com/51139868/214158071-50cc0e74-0d01-4222-83e3-a503d24baa0f.png)

angoose



