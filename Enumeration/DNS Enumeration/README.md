# DNS Enumeration

DNS enumeration is the process of gathering information about DNS (Domain Name System) servers and their associated records for a target domain. This information can be valuable for reconnaissance and vulnerability assessment purposes. DNS enumeration involves querying DNS servers to extract various types of information, including domain names, IP addresses, mail servers, and more.

## Types of DNS Records

1. **A Records (Address Records):** Maps domain names to IPv4 addresses.
2. **AAAA Records (IPv6 Address Records):** Maps domain names to IPv6 addresses.
3. **CNAME Records (Canonical Name Records):** Alias of one domain to another.
4. **MX Records (Mail Exchange Records):** Specifies the mail server responsible for receiving email on behalf of the domain.
5. **NS Records (Name Server Records):** Identifies the authoritative DNS servers for the domain.
6. **PTR Records (Pointer Records):** Maps IP addresses to domain names (reverse DNS lookup).
7. **TXT Records (Text Records):** Contains miscellaneous information about the domain.

## DNS Enumeration Techniques

### Zone Transfer

Zone transfer (AXFR) is a mechanism that allows a secondary DNS server to copy the entire zone data from a primary DNS server. It can provide valuable information about all the DNS records in the zone.

Example:

```bash
dig axfr example.com @ns1.example.com 
```


# DNS Lookup

Performing DNS lookups using tools like nslookup, dig, or host can reveal various DNS records associated with a domain.

Example:

```bash
nslookup example.com 
```
# Brute Force

Brute-forcing subdomains involves guessing and querying for non-existent or hidden subdomains within a domain. This can be done using tools like dnsenum, dnsrecon, or custom scripts.

Example:

```bash
dnsrecon -d example.com -t std
```
# DNS Cache Snooping





