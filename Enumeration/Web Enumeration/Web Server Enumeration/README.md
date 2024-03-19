# Web Server Enumeration

Web server enumeration focuses on identifying information about the target web server, including its software, version, and potential vulnerabilities. This information can help in understanding the attack surface and planning further exploitation strategies.

## 1. Banner Grabbing

Banner grabbing is the process of retrieving HTTP header information from the web server to identify details such as the server software and version. This information is often available in the server response headers and can provide valuable insights into the underlying technology stack.

### Example:
```bash
curl -I http://example.com
```

or

```bash
wget -S --spider http://example.com
```

## 2. Web Server Fingerprinting
Web server fingerprinting involves identifying the type of web server, programming languages, frameworks, and technologies used by analyzing various characteristics of the HTTP responses.

### Example Tools:
nmap
WhatWeb
Wappalyzer


### Nmap Scripts:
Nmap provides a variety of scripts specifically designed for web server enumeration. Here are some examples:

Usage:
```bash
nmap -sV --script=http-fingerprint example.com
```

- **http-headers: Retrieves HTTP headers from web servers.
- **http-server-header: Extracts server banners from HTTP headers.
- **http-title: Retrieves the title of the web page.
- **http-php-version: Detects the PHP version used by the web server.
- **http-apache-server-status: Checks for the presence of Apache server status pages.
- **http-robots.txt: Retrieves robots.txt file from web servers.
- **http-comments-displayer: Displays HTML comments found in web pages.
- **http-config-backup: Searches for backup files of web server configurations.

These Nmap scripts can be used to gather detailed information about the target web server and its configuration, helping in identifying potential vulnerabilities and attack vectors.

### WhatWeb:

```bash
whatweb example.com

```
Web server fingerprinting helps in understanding the technology stack of the web server, which can assist in identifying potential vulnerabilities and attack vectors.
