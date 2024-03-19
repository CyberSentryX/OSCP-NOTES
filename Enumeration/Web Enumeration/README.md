# Web Enumeration Guide

Web enumeration is the process of gathering information about a web application to identify potential attack vectors and vulnerabilities. It involves various techniques to explore the web application's structure, technologies used, and potential entry points for attacks.

## Part 1: Information Gathering

### 1. DNS Enumeration

- Use tools like `nslookup` or `dig` to gather information about the domain's DNS records, including subdomains and associated IP addresses.

### 2. WHOIS Lookup

- Perform a WHOIS lookup to gather information about the domain owner, registrar, registration date, and contact information.

### 3. Subdomain Enumeration

- Use tools like `Sublist3r`, `Amass`, or `OWASP Amass` to discover subdomains associated with the target domain.

## Part 2: Web Server Enumeration

### 1. Banner Grabbing

- Use tools like `curl` or `wget` to retrieve the HTTP header information from the web server, including server software and version.

### 2. Web Server Fingerprinting

- Use tools like `nmap`, `WhatWeb`, or `Wappalyzer` to identify the web server type, programming languages, frameworks, and technologies used.

## Part 3: Directory and File Enumeration

### 1. Directory Brute-Forcing

- Use tools like `DirBuster`, `DirSearch`, or `Gobuster` to brute-force directories and files on the web server.

### 2. Common File Discovery

- Enumerate common files and directories like `/robots.txt`, `/sitemap.xml`, `/admin`, `/login`, etc., for potential entry points.

## Part 4: Web Application Enumeration

### 1. Spidering

- Use tools like `Burp Suite`, `ZAP`, or `Wget` with recursive crawling to spider the entire website and discover hidden or dynamically generated content.

### 2. Parameter Enumeration

- Identify input parameters in web forms, URLs, and cookies, and manipulate them to test for vulnerabilities like SQL injection, XSS, etc.

## Part 5: Technologies and Services Enumeration

### 1. JavaScript Libraries

- Use browser extensions like `Wappalyzer` or examine page source code to identify JavaScript libraries, frameworks, and plugins used.

### 2. Web Application Firewall (WAF) Detection

- Use tools like `Nmap`, `WafW00f`, or `WhatWeb` to detect if the web application is protected by a WAF and its type.

## Part 6: Authentication Mechanisms Enumeration

### 1. Username Enumeration

- Test login forms to determine if they disclose valid usernames through error messages or response timing.

### 2. Password Policy Enumeration

- Identify password policy restrictions, such as minimum length, complexity requirements, and lockout policies.

## Part 7: Error Handling Enumeration

### 1. Error Code Analysis

- Analyze HTTP error codes to identify potential vulnerabilities or misconfigurations in the web application.

### 2. Information Leakage

- Look for sensitive information leakage in error messages, stack traces, or debug mode responses.

## Part 8: Content Management System (CMS) Enumeration

### 1. CMS Identification

- Use tools like `CMSmap` or analyze response headers to identify the CMS used by the web application.

### 2. Plugin and Theme Enumeration

- Enumerate installed plugins and themes to identify known vulnerabilities or attack vectors.

## Part 9: API Enumeration

### 1. API Endpoint Discovery

- Use tools like `Swagger`, `OpenAPI`, or manual testing to discover exposed API endpoints and their functionality.

### 2. Authentication Mechanisms

- Identify authentication mechanisms used by the API, such as API keys, OAuth tokens, or JWT tokens.

## Part 10: Reporting and Documentation

- Document all findings, including discovered vulnerabilities, misconfigurations, and potential attack vectors.
- Prioritize vulnerabilities based on severity and impact to assist in remediation efforts.
- Provide recommendations and mitigations to address identified security issues.

