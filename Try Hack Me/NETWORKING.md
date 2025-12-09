DHCP is an application-level protocol that relies on UDP; the server listens on UDP port 67, and the client sends from UDP port 68.

Ping uses ICMP protocol

Ethernet (IEEE 802.3) and WiFi (IEEE 802.11)

Address Resolution Protocol (ARP) , Internet Control Messaging Protocol

nslookup - Find ip address of the Domain

Internet Message Access Protocol (IMAP).

Executing `chromium --ssl-key-log-file=~/ssl-key.log` dumps the TLS keys to the `ssl-key.log` file.

ipam - ip address management

  

|**Protocol**|**Transport Protocol**|**Default Port Number**|
|---|---|---|
|TELNET|TCP|23|
|DNS|UDP or TCP|53|
|HTTP|TCP|80|
|HTTPS|TCP|443|
|FTP|TCP|21|
|SMTP|TCP|25|
|POP3|TCP|110|
|IMAP|TCP|143|
|SMTPS|TCP|465 & 587|
|POP3S|TCP|995|
|IMAPS|TCP|993|
|RDP|TCP|3389|

---

SMTP Protocol :

- `HELO` or `EHLO` initiates an SMTP session

- `MAIL FROM` specifies the sender’s email address

- `RCPT TO` specifies the recipient’s email address

- `DATA` indicates that the client will begin sending the content of the email message

- `.` is sent on a line by itself to indicate the end of the email message

---

POP3(Post Office Protocol) Commands: port -110

  

AUTH , USER <Username> , PASS <Password>

- `USER <username>` identifies the user

- `PASS <password>` provides the user’s password

- `STAT` requests the number of messages and total size

- `LIST` lists all messages and their sizes

- `RETR <message_number>` retrieves the specified message

- `DELE <message_number>` marks a message for deletion

- `QUIT` ends the POP3 session applying changes, such as deletions
    
    ---
    

IMAP Protocol

- `LOGIN <username> <password>` authenticates the user

- `SELECT <mailbox>` selects the mailbox folder to work with

- `FETCH <mail_number> <data_item_name>` Example `fetch 3 body[]` to fetch message number 3, header and body.

- `MOVE <sequence_set> <mailbox>` moves the specified messages to another mailbox

- `COPY <sequence_set> <data_item_name>` copies the specified messages to another mailbox

- `LOGOUT` logs out

---

## DNS: Remembering Addresses

A record -hostname or ipv4

AAAA record - ipv6

CNAME Record- to another domain name

mx record - mail server  

---

## Routing algorithms

  

- **OSPF (Open Shortest Path First):** A link-state protocol that enables routers within the same organization to calculate the shortest, most efficient internal network routes.

- **EIGRP (Enhanced Interior Gateway Routing Protocol):** A Cisco-developed hybrid protocol that efficiently finds optimal internal paths based on multiple route metrics, combining features of distance-vector and link-state methods

- **BGP (Border Gateway Protocol):** An exterior routing protocol used on the Internet to exchange routing information and decide routes between different organizations or autonomous systems

- **RIP (Routing Information Protocol):** A simple, distance-vector protocol using hop count as its metric, best for small networks due to limited scalability and slow convergence