## froxbuster

[froxbuster](https://github.com/epi052/feroxbuster)
[official documentation](https://epi052.github.io/feroxbuster-docs/docs/)


##### install

```shell
sudo apt update && sudo apt install -y feroxbuster
```

##### update

```shell
./feroxbuster --update
```

##### Multiple Values

Options that take multiple values are very flexible. Consider the following ways of specifying extensions:
The command adds .pdf, .js, .html, .php, .txt, .json, and .docx to each url
All of the methods (multiple flags, space separated, comma separated, etc...) are valid and interchangeable. The same goes for urls, headers, status codes, queries, and size filters.

```bash
./feroxbuster -u http://127.1 -x pdf -x js,html -x php txt json,docx
```

##### Include Headers

```bash
./feroxbuster -u http://127.1 -H Accept:application/json "Authorization: Bearer {token}"
```

##### IPv6, non-recursive scan with INFO-level logging enabled

```bash
./feroxbuster -u http://[::1] --no-recursion -vv
```

##### Read urls from STDIN; pipe only resulting urls out to another tool

```bash
cat targets | ./feroxbuster --stdin --silent -s 200 301 302 --redirects -x js | fff -s 200 -o js-files
```

##### Proxy traffic through Burp

```bash
./feroxbuster -u http://127.1 --insecure --proxy http://127.0.0.1:8080
```

##### Proxy traffic through a SOCKS proxy (including DNS lookups)

```bash
./feroxbuster -u http://127.1 --proxy socks5h://127.0.0.1:9050
```

##### Pass auth token via query parameter
```bash
./feroxbuster -u http://127.1 --query token=0123456789ABCDEF
```