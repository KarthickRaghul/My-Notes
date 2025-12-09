Diffie-Hellman Key Exchange - Symmetric Encryption  
public key : _A_ = _g^a_ mod _p , B_ = _g^b_ mod _p , private key : B^a_ mod _p , A^b_ mod _p_ 

- **DSA (Digital Signature Algorithm)** is a public-key cryptography algorithm specifically designed for digital signatures.

- **ECDSA (Elliptic Curve Digital Signature Algorithm)** is a variant of DSA that uses elliptic curve cryptography to provide smaller key sizes for equivalent security.

- **ECDSA-SK (ECDSA with Security Key)** is an extension of ECDSA. It incorporates hardware-based security keys for enhanced private key protection.

- **Ed25519** is a public-key signature system using EdDSA (Edwards-curve Digital Signature Algorithm) with Curve25519.

- **Ed25519-SK (Ed25519 with Security Key)** is a variant of Ed25519. Similar to ECDSA-SK, it uses a hardware-based security key for improved private key protection.

GPG is commonly used in email to protect the confidentiality of the email messages

  

[https://crackstation.net/](https://crackstation.net/)

[https://hashes.com/en/decrypt/hash](https://hashes.com/en/decrypt/hash)

[https://pypi.org/project/hashID/](https://pypi.org/project/hashID/) - Automatic hash finder

[https://hashcat.net/wiki/doku.php?id=example_hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)

  

`man 5 shadow`

`man 5 crypt` - command

  

MS Windows passwords are hashed using NTLM, a variant of MD4

On MS Windows, password hashes are stored in the SAM (Security Accounts Manager). MS Windows tries to prevent normal users from dumping them, but tools like mimikatz exist to circumvent MS Windows security. Notably, the hashes found there are split into NT hashes and LM hashes.

On Linux, password hashes are stored in `/etc/shadow`

format `$prefix$options$salt$hash`

  

|Prefix|Algorithm|
|---|---|
|`$y$`|yescrypt is a scalable hashing scheme and is the default and recommended choice in new systems|
|`$gy$`|gost-yescrypt uses the GOST R 34.11-2012 hash function and the yescrypt hashing method|
|`$7$`|scrypt is a password-based key derivation function|
|`$2b$`, `$2y$`, `$2a$`, `$2x$`|bcrypt is a hash based on the Blowfish block cipher originally  <br>developed for OpenBSD but supported on a recent version of FreeBSD,  <br>NetBSD, Solaris 10 and newer, and several Linux distributions|
|`$6$`|sha512crypt is a hash based on SHA-2 with 512-bit output originally developed for GNU libc and commonly used on (older) Linux systems|
|`$md5`|SunMD5 is a hash based on the MD5 algorithm originally developed for Solaris|
|`$1$`|md5crypt is a hash based on the MD5 algorithm originally developed for FreeBSD|

The following steps give you a fair idea of how HMAC works.

1. The secret key is padded to the block size of the hash function.

1. The padded key is XORed with a constant (usually a block of zeros or ones).

1. The message is hashed using the hash function with the XORed key.

1. The result from Step 3 is then hashed again with the same hash function but using the padded key XORed with another constant.

1. The final output is the HMAC value, typically a fixed-size string.

the HMAC function is calculated using the following expression:

_HMAC_(_K_,_M_) = _H_((_K_⊕_opad_)||_H_((_K_⊕_ipad_)||_M_))

Note that M and K represent the message and the key,