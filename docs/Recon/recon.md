# recon

[DNSdumpster](https://dnsdumpster.com/)
[Shodan.io](https://www.shodan.io/)

```shell
whois
ping
telnet
traceroute
nc
```

```shell
#We can use the favicon link of a website to find the framework used
curl https://website.com/favicon.ico | md5sum
#this calculates md5 hash value after downloading the favicon
#hash can be used to lookup on <https://wiki.owasp.org/index.php/OWASP_favicon_database>
```

```shell
#Manually discovering HTTP headers
curl http://website.com/ -v
```


Google dorking

