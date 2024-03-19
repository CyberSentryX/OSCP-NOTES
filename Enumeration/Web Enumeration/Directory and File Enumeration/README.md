# Part 3: Directory and File Enumeration

When conducting web enumeration, exploring directories and discovering common files is crucial for identifying potential entry points and gaining insights into the web application's structure and content.

## 1. Directory Brute-Forcing

Directory brute-forcing involves systematically guessing directory and file paths on the web server to discover hidden or unlinked resources. Tools like `DirBuster`, `DirSearch`, or `Gobuster` automate this process by sending HTTP requests to different paths and analyzing the server's responses.

Directory brute-forcing helps uncover directories and files that are not linked from the web application's main pages but may still be accessible. These hidden resources may contain sensitive information or provide entry points for further enumeration and exploitation.

Example:

### 1. Dirsearch Tool

Dirsearch is a powerful tool for brute-forcing directories and files on web servers.

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

Feroxbuster is a tool designed for directory and file brute-forcing on web servers. It is similar to other directory brute-forcing tools like DirBuster and Dirsearch but offers some unique features and advantages. Here's an explanation of Feroxbuster:

#### Usage:
- Feroxbuster can be used from the command line interface. Here's a basic usage example:

 ```bash
feroxbuster -u http://example.com -w /path/to/wordlist.txt
 ```
-u: Specifies the target URL to scan.
-w: Specifies the path to the wordlist to use for brute-forcing.


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


### 3. Dirb Tool

Dirb is a popular web application scanner designed to facilitate directory and file brute-forcing on web servers. It helps identify hidden directories and files that may be vulnerable to attacks such as information disclosure, unauthorized access, and directory traversal. Here's an overview of Dirb:

#### Usage:
Dirb can be used from the command line interface. Here's a basic usage example:

 ```bash
dirb http://example.com /path/to/wordlist.txt
 ```
The first argument (http://example.com) specifies the target URL to scan.
The second argument (/path/to/wordlist.txt) specifies the path to the wordlist to use for brute-forcing.

 ```bash
dirb http://example.com /path/to/wordlist.txt
 ```

- Specify the number of threads:

 ```bash
dirb http://example.com /path/to/wordlist.txt -r -T 100
 ```

- Recursive scanning:

 ```bash
dirb http://example.com /path/to/wordlist.txt -r
 ```

- Save output to a file:

 ```bash
dirb http://example.com /path/to/wordlist.txt -o /path/to/output.txt
 ```


### 4. Gobuster Tool

Gobuster is a tool used for directory and file brute-forcing on web servers. It is designed to help identify hidden directories and files that may be vulnerable to attacks such as unauthorized access, information disclosure, and directory traversal. Here's an overview of Gobuster:

#### Usage:
Gobuster can be used from the command line interface. Here's a basic usage example:

 ```bash

gobuster dir -u http://example.com -w /path/to/wordlist.txt
 ```
The dir command specifies that we want to perform directory brute-forcing.
The -u http://example.com option specifies the target URL to scan.
The -w /path/to/wordlist.txt option specifies the path to the wordlist to use for brute-forcing.

 ```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt
 ```

- Specify the number of threads:

 ```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -t 100
 ```

- Recursive scanning:

 ```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -r
 ```

- Save output to a file:

 ```bash
gobuster dir -u http://example.com -w /path/to/wordlist.txt -o /path/to/output.txt
 ```


### 5. Wfuzz Tool

Wfuzz is a versatile web application fuzzer that is used for brute-forcing web applications. It can help identify vulnerabilities such as SQL injection, XSS, directory traversal, and more. Here's an overview of Wfuzz:

#### Usage:
Wfuzz can be used from the command line interface. Here's a basic usage example:

 ```bash
wfuzz -c -z file,/path/to/wordlist.txt --hc 404 http://example.com/FUZZ
 ```

The -c option specifies to colorize output for better readability.
The -z file,/path/to/wordlist.txt option specifies the wordlist to use for fuzzing.
The --hc 404 option specifies to hide responses with HTTP status code 404 (Not Found).
The URL http://example.com/FUZZ contains the keyword FUZZ, which will be replaced by payloads from the wordlist.


 ```bash
wfuzz -c -z file,/path/to/wordlist.txt http://example.com/FUZZ
 ```

- Specify the number of threads:

 ```bash
wfuzz -c -z file,/path/to/wordlist.txt -t 100 http://example.com/FUZZ
 ```

- Filter responses by status code:

 ```bash
wfuzz -c -z file,/path/to/wordlist.txt --hc 200,301 http://example.com/FUZZ
 ```

- Save output to a file:

 ```bash
wfuzz -c -z file,/path/to/wordlist.txt -o /path/to/output.txt http://example.com/FUZZ
 ```



## 2. Common File Discovery

Common file discovery involves enumerating standard files and directories commonly found on web servers. These files often provide valuable information about the web application's configuration, functionality, and potential vulnerabilities.

Enumerating common files and directories like /robots.txt, /sitemap.xml, /admin, /login, etc., can reveal hidden functionalities, administrative interfaces, or sensitive information that may be overlooked.

Example:

 ```bash
curl http://example.com/robots.txt
 ```

 ```bash
curl http://example.com/sitemap.xml
 ```
 
 ```bash
curl http://example.com/admin
 ```
 
 ```bash
curl http://example.com/login
 ```



## 2. Parameter Fuzzzing 

Parameter Fuzzing is a technique used to discover vulnerabilities in web applications by testing different parameters with various payloads. It involves systematically injecting payloads into input fields, headers, or other parts of a request to identify potential security flaws, such as SQL injection, cross-site scripting (XSS), command injection, and more. Here are some examples of using popular parameter fuzzing tools:

### 1. wfuzz

- Syntax:
 ```bash
wfuzz -z file,<payload_file> <target_URL>
 ```

- Example:
 ```bash
wfuzz -z file,fuzz-lfi-param http://192.168.241.229/index.php?FUZZ
 ```

### 2. ffuf

- Syntax:
 ```bash
ffuf -w <payload_file> -u <target_URL>?FUZZ=<payload> -fs <error_code>
 ```

- Example:
 ```bash
ffuf -w fuzz-lfi-param -u http://192.168.241.229/index.php?FUZZ=/etc/passwd -fs 3151
 ```

### 3. Arjun

- Syntax:
 ```bash
arjun -u <target_URL> -w <payload_file>
 ```

- Example:
 ```bash
arjun -u http://192.168.241.229/index.php -w fuzz-lfi-param
 ```
