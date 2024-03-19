# Part 1: Information Gathering

In this part, we focus on gathering information about the target domain to understand its infrastructure and ownership.

## 1. DNS Enumeration

DNS enumeration involves querying DNS servers to gather information about the domain's DNS records, including subdomains and associated IP addresses. This information can help identify potential attack vectors and services hosted on the domain.

### Example:
```bash
nslookup example.com

or

dig example.com
```

## 2. WHOIS Lookup
A WHOIS lookup provides information about the domain owner, registrar, registration date, and contact information. This information can help identify the organization behind the domain and its administrative contacts.

### Example:
```bash
whois example.com
```

## 3. Subdomain Enumeration
Subdomain enumeration involves discovering subdomains associated with the target domain. Subdomains may represent different services or departments within an organization, providing additional attack surface for attackers.

### Example Tools:
Sublist3r
Amass
OWASP Amass

### Example Usage:
```bash
sublist3r -d example.com
```
Subdomain enumeration helps identify all publicly accessible subdomains associated with the target domain, allowing further exploration and potential attack vectors.







