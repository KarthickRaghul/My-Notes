Check all the endpoint

change the http methods of the endpoints

change the content type of the data provided in a request

HTTP Methods:

Get,Post,Put,Patch,Delete,Head,Options,Connect,Trace

- `/api`

- `/swagger/index.html`

- `/openapi.json`

- `/api/swagger/v1`

  

Bapp - Param miner (helps to replace the param names) , Backslash Powered Scanne - dentify server-side injection vulnerabilities

  

Mass Assignment params :

role , isAdmin , is_verified , price , owner_id , status , approved

  

## Truncating query strings

You can use a URL-encoded `#` character to attempt to truncate the server-side request. To help you interpret the response, you could also add a string after the `#` character.

To test for server-side parameter pollution in the query string, place query syntax characters like `#`,  
`&`, and `=`

  

- PHP parses only the last parameter.

- [ASP.NET](http://asp.net/) combines both parameters.

- Node.js/Express parses only the first parameter.