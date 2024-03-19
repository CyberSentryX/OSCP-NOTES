# Part 3: Directory and File Enumeration

When conducting web enumeration, exploring directories and discovering common files is crucial for identifying potential entry points and gaining insights into the web application's structure and content.

## 1. Directory Brute-Forcing

Directory brute-forcing involves systematically guessing directory and file paths on the web server to discover hidden or unlinked resources. Tools like `DirBuster`, `DirSearch`, or `Gobuster` automate this process by sending HTTP requests to different paths and analyzing the server's responses.

Directory brute-forcing helps uncover directories and files that are not linked from the web application's main pages but may still be accessible. These hidden resources may contain sensitive information or provide entry points for further enumeration and exploitation.

Example:

### 1. Dirsearch Tool

Dirsearch is a powerful tool for brute-forcing directories and files on web servers.

#### Configuration Files

- `/etc/dirsearch/default.conf`: Dirsearch configuration file.
- `/usr/lib/python3/dist-packages/dirsearch/db/dicc.txt`: Dirsearch default wordlist.
- `/usr/share/seclists/Discovery/Web-Content/dirsearch.txt`: Dirsearch default wordlist provided by SecLists.
- `~/.dirsearch/reports`: By default, Dirsearch saves output reports to this location.

#### Usage Examples

- Basic usage:
 ```bash
 dirsearch -u example.com
```
  
- Use a proxy (e.g., Burp Suite):
 ```bash
  dirsearch -u example.com -t 100 --proxy=127.0.0.1:8080
 ```

- Define the number of threads:

 ```bash
  dirsearch -u example.com -t 100
 ```
- Specify a custom wordlist:

 ```bash
  dirsearch -u example.com -w /path/to/custom/wordlist.txt -t 100
 ```

- Recursive directory scanning:

 ```bash
  dirsearch -u example.com -w /path/to/wordlist.txt -r -t 100
 ```

- Define specific file extensions:

 ```bash
  dirsearch -u example.com -w /path/to/wordlist.txt -e "*" -t 100
 ```

- Filter HTTP status codes:

 ```bash
  dirsearch -u example.com -w /path/to/wordlist.txt -f -x 403,301,500-599 -t 100
 ```

- Specify a custom HTTP method (e.g., POST):

 ```bash
  dirsearch -u example.com -w /path/to/wordlist.txt --http-method=POST -t 100
 ```

- Save output to a specific location:

 ```bash
  dirsearch -u example.com -i 403 -o /path/to/output/dirsearch.txt
 ```

### 2. Feroxbuster Tool

#### Usage:
- Feroxbuster can be used from the command line interface. Here's a basic usage example:

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt
-u: Specifies the target URL to scan.
-w: Specifies the path to the wordlist to use for brute-forcing.
 ```

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt
 ```

- Specify the number of threads:

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt -t 100
 ```
- Recursive scanning:

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt -r
 ```
- Save output to a file:

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt -o /path/to/output.txt
 ```
