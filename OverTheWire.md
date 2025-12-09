Bandits:

[[Passwords]]

Natas:

[[passwords]]

  
  
`export TERM=xterm-256color`

blog - [https://mayadevbe.me/posts/overthewire/bandit/overview/](https://mayadevbe.me/posts/overthewire/bandit/overview/)

  

xxd - related with hexdumps

---

`scp -P <port> <user>@<IP>:<remotefilepath> <localfilepath>` - file transfer over ssh

or we can start a web server using python - `python3 -m http.server` (best is to do it in the directory of the file). On the receiving machine you then just have to send an HTTP request: `wget http://<ip>:8000/<pathtofile>`

---

for ssh -i the rsa key should be of the permission bit 700

---

Automation for openSSl - [https://www.hardenize.com/](https://www.hardenize.com/) , [https://testssl.sh/](https://testssl.sh/)

---

SUID - If a file has the **SUID bit**, when someone runs it, it runs **as the file’s owner**, not as the person who runs it. Format : rwsr-xr-x (insted of x there will be s )

SGID - works like SUID, but for **groups** instead of users. Format : -rwxr-sr-x (s in groups)

Stickt Bit - **Only the file’s owner (or root)** can delete or rename the file — even if others have write access. Format : drwxrwxrwt (t at the end)

chmod 4755 filename

The 4 in front means “add SUID”.  
So: 4 = SUID  
2 = SGID  
1 = Sticky bit

---

etc/services - contains all the open ports and the details the port is related with