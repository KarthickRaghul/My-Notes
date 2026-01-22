
❯ nmap 10.129.97.139                 
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-22 11:40 +0530
Warning: 10.129.97.139 giving up on port because retransmission cap hit (10).
Nmap scan report for 10.129.97.139
Host is up (0.39s latency).
Not shown: 993 closed tcp ports (conn-refused)
PORT      STATE    SERVICE
22/tcp    open     ssh
514/tcp   filtered shell
625/tcp   filtered apple-xsrvr-admin
5280/tcp  filtered xmpp-bosh
9000/tcp  filtered cslistener
10010/tcp filtered rxapi
26214/tcp filtered unknown


---



~ took 9s 
❯ hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://10.129.97.139 -t 4
Hydra v9.6 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2026-01-22 12:16:38
[DATA] max 4 tasks per 1 server, overall 4 tasks, 14344398 login tries (l:1/p:14344398), ~3586100 tries per task
[DATA] attacking ssh://10.129.97.139:22/
[ERROR] all children were disabled due too many connection errors
0 of 1 target completed, 0 valid password found
[INFO] Writing restore file because 2 server scans could not be completed
[ERROR] 1 target was disabled because of too many errors
[ERROR] 1 targets did not complete
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2026-01-22 12:17:10


---


~ 
❯       nmap -p22 -sV --script ssh2-enum-algos,ssh-hostkey 10.129.97.139
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-22 13:06 +0530
Nmap scan report for 10.129.97.139
Host is up (0.39s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 10.0p2 Debian 8 (protocol 2.0)
| ssh2-enum-algos: 
|   kex_algorithms: (10)
|       mlkem768x25519-sha256
|       sntrup761x25519-sha512
|       sntrup761x25519-sha512@openssh.com
|       curve25519-sha256
|       curve25519-sha256@libssh.org
|       ecdh-sha2-nistp256
|       ecdh-sha2-nistp384
|       ecdh-sha2-nistp521
|       ext-info-s
|       kex-strict-s-v00@openssh.com
|   server_host_key_algorithms: (4)
|       rsa-sha2-512
|       rsa-sha2-256
|       ecdsa-sha2-nistp256
|       ssh-ed25519
|   encryption_algorithms: (6)
|       chacha20-poly1305@openssh.comq
|       aes128-gcm@openssh.com
|       aes256-gcm@openssh.com
|       aes128-ctr
|       aes192-ctr
|       aes256-ctr
|   mac_algorithms: (10)
|       umac-64-etm@openssh.com
|       umac-128-etm@openssh.com
|       hmac-sha2-256-etm@openssh.com
|       hmac-sha2-512-etm@openssh.com
|       hmac-sha1-etm@openssh.com
|       umac-64@openssh.com
|       umac-128@openssh.com
|       hmac-sha2-256
|       hmac-sha2-512
|       hmac-sha1
|   compression_algorithms: (2)
|       none
|_      zlib@openssh.com
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 15.70 seconds

---

❯ sudo nmap -sU --top-ports 100 -T4 --max-retries 2 -n 10.129.97.139
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-22 13:54 +0530
Warning: 10.129.97.139 giving up on port because retransmission cap hit (2).
Nmap scan report for 10.129.97.139
Host is up (0.21s latency).
Not shown: 92 open|filtered udp ports (no-response)
PORT      STATE  SERVICE
7/udp     closed echo
9/udp     closed discard
500/udp   open   isakmp
1645/udp  closed radius
1812/udp  closed radius
5000/udp  closed upnp
49194/udp closed unknown
49201/udp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 9.32 seconds


---
❯ sudo nmap -sV -sU 10.129.97.139 
Nmap scan report for 10.129.97.139
Host is up (0.40s latency).
Not shown: 996 closed udp ports (port-unreach)
PORT     STATE         SERVICE   VERSION
68/udp   open|filtered dhcpc
69/udp   open|filtered tftp
500/udp  open          isakmp?
4500/udp open|filtered nat-t-ike
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port500-UDP:V=7.98%I=7%D=1/22%Time=6971DFD2%P=x86_64-pc-linux-gnu%r(IKE
SF:_MAIN_MODE,70,"\0\x11\"3DUfwO\x8eR\xce\x91u\x20\x81\x01\x10\x02\0\0\0\0
SF:\0\0\0\0p\r\0\x004\0\0\0\x01\0\0\0\x01\0\0\0\(\x01\x01\0\x01\0\0\0\x20\
SF:x01\x01\0\0\x80\x01\0\x05\x80\x02\0\x02\x80\x04\0\x02\x80\x03\0\x01\x80
SF:\x0b\0\x01\x80\x0c\0\x01\r\0\0\x0c\t\0&\x89\xdf\xd6\xb7\x12\0\0\0\x14\x
SF:af\xca\xd7\x13h\xa1\xf1\xc9k\x86\x96\xfcwW\x01\0")%r(IPSEC_START,9C,"1'
SF:\xfc\xb08\x10\x9e\x89\xfc\xdazA\xa7\xa2X\x8d\x01\x10\x02\0\0\0\0\0\0\0\
SF:0\x9c\r\0\x004\0\0\0\x01\0\0\0\x01\0\0\0\(\x01\x01\0\x01\0\0\0\x20\x01\
SF:x01\0\0\x80\x01\0\x05\x80\x02\0\x02\x80\x04\0\x02\x80\x03\0\x03\x80\x0b
SF:\0\x01\x80\x0c\x0e\x10\r\0\0\x0c\t\0&\x89\xdf\xd6\xb7\x12\r\0\0\x14\xaf
SF:\xca\xd7\x13h\xa1\xf1\xc9k\x86\x96\xfcwW\x01\0\r\0\0\x18@H\xb7\xd5n\xbc
SF:\xe8\x85%\xe7\xde\x7f\0\xd6\xc2\xd3\x80\0\0\0\0\0\0\x14\x90\xcb\x80\x91
SF:>\xbbin\x08c\x81\xb5\xecB{\x1f");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1423.30 seconds


---
https://www.verylazytech.com/network-pentesting/ipsec-ike-vpn-port-500-udp
---


❯ sudo nmap -sU -p 500 --script ike-version 10.129.97.139
[sudo] password for karthi: 
Starting Nmap 7.98 ( https://nmap.org ) at 2026-01-22 14:54 +0530
Nmap scan report for 10.129.97.139
Host is up (0.21s latency).

PORT    STATE SERVICE
500/udp open  isakmp
| ike-version: 
|   attributes: 
|     XAUTH
|_    Dead Peer Detection v1.0

Nmap done: 1 IP address (1 host up) scanned in 1.41 seconds