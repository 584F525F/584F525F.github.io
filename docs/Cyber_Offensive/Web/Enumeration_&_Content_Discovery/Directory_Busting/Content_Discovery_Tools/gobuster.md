[gobuster](https://github.com/OJ/gobuster)

**Used to brute-force:**
- URIs (directories and files) in web sites.
- DNS subdomains (with wildcard support).
- Virtual Host names on target web servers.
- Open Amazon S3 buckets
- Open Google Cloud buckets
- TFTP servers



```shell
#dir Mode - the classic directory brute-forcing mode
gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt

#With content length - the classic directory brute-forcing mode
gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt -l

----------------------------------------------------------------------------------------
#dns Mode - DNS subdomain brute-forcing mode
gobuster dns -d example.com -t 50 -w common-names.txt
gobuster dns -d example.com-w ~/wordlists/subdomains.txt

#With Show IP - DNS subdomain brute-forcing mode
gobuster dns -d example.com -w ~/wordlists/subdomains.txt -i

#Base domain validation warning when the base domain fails to resolve
gobuster dns -d example.com -w ~/wordlists/subdomains.txt -i

#Wildcard DNS is also detected properly:
gobuster dns -d 0.0.1.xip.io -w ~/wordlists/subdomains.txt


-h,	--help	help for dns
-d,	--domain string	The target domain
-r,	--resolver string	Use custom DNS server (format server.com or server.com:port)
-c,	--show-cname	Show CNAME records (cannot be used with '-i' option)
-i,	--show-ips	Show IP addresses
--timeout duration	DNS resolver timeout (default 1s)


----------------------------------------------------------------------------------------
#vhost Mode - Virtual host brute-forcing mode (not the same as DNS!)
gobuster vhost -u https://example.com -w common-vhosts.txt


-h	--help	help for vhost
-c	--cookies string	Cookies to use for the requests
-r	--follow-redirect	Follow redirects
-H	--headers stringArray	Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
-k	--no-tls-validation	Skip TLS certificate verification
-P	--password string	Password for Basic Auth
-p	--proxy string	Proxy to use for requests [http(s)://host:port]
--timeout duration	HTTP Timeout (default 10s)
-u	--url string	The target URL
-a	--useragent string	Set the User-Agent string (default "gobuster/3.1.0")
-U	--username string	Username for Basic Auth
-h	--help	help for vhost
-c	--cookies string	Cookies to use for the requests
-r	--follow-redirect	Follow redirects
-H	--headers stringArray	Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'
-k	--no-tls-validation	Skip TLS certificate verification
-P	--password string	Password for Basic Auth
-p	--proxy string	Proxy to use for requests [http(s)://host:port]
--timeout duration	HTTP Timeout (default 10s)
-u	--url string	The target URL
-a	--useragent string	Set the User-Agent string (default "gobuster/3.1.0")
-U	--username string	Username for Basic Auth


----------------------------------------------------------------------------------------
#s3 Mode - Enumerate open S3 buckets and look for existence and bucket listings
gobuster s3 -w bucket-names.txt

#global flags
-z	--no-progress	Don't display progress
-o	--output string	Output file to write results to (defaults to stdout)
-q	--quiet	Don't print the banner and other noise
-t	--threads int	Number of concurrent threads (default 10)
-i	--show-ips	Show IP addresses
--delay duration	DNS resolver timeout (default 1s)
-v,	--verbose	Verbose output (errors)
-w	--wordlist string	Path to the wordlist 
```
