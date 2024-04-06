Chameleon - Context-Aware Content Discovery

[Chameleon](https://github.com/iustin24/chameleon)

### Commands

##### install
```shell
curl -sL https://raw.githubusercontent.com/iustin24/chameleon/master/install.sh | bash
```
##### Tech Scan + Directory Bruteforce:
```shell
chameleon --url https://example.com -a
```

### Config file

Chameleon uses the config file located in ~/.config/chameleon/config.yaml.

##### Changing the default wordlists:

If no wordlist is provided, chameleon will use the wordlist specified in main_wordlist from the config file. ( Default: ~/.config/chameleon/wordlists/raft-medium-words.txt )

When detecting technologies with characteristic extensions, chameleon will generate a wordlist by like so ( FUZZ.%ext ). Chameleon will use the wordlist specified in small_wordlist from the config file. ( Default: ~/.config/chameleon/wordlists/raft-medium-words.txt )

##### Changing technology wordlists

Example config.yaml with technology specific wordlists:

```shell
#Technology Specific Wordlists:
Flask="~/.config/chameleon/wordlists/Flask.txt"
Java="~/.config/chameleon/wordlists/Java.txt"
Go="~/.config/chameleon/wordlists/GO.txt"
```

##### Adding new technology wordlists

Chameleon uses fingerprints from https://github.com/iustin24/wappalyzer/blob/master/apps.json. You can add new technology wordlists by taking the name of a technology from apps.json and adding it to the config file like so:
```bash
# Technology Specific Wordlists:

1C-Bitrix="~/.config/chameleon/wordlists/new_tech_wordlist.txt"
```
##### Adding new extension fingerprints.
```bash
# Technology specific Extensions

Microsoft_ASP_NET_ext="aspx,ashx,asmx,asp"
Java_ext="jsp"
CFML_ext="cfm"
Python_ext="py"
PHP_ext="php"
```

### Switches | Options

```bash
OPTIONS:
    -a, --tech-detect
            Automatically detect technologies with wappalyzer and adapt wordlist

    -A, --auto-calibrate
            Automatically calibrate filtering options (default: false)

    -c, --mc <MATCHCODE>...
            Match HTTP status codes from response - Comma separated list [default:
            200,204,301,302,307,401,403,405]

    -C, --fc <FILTERCODE>...
            Filter HTTP status codes from response - Comma separated list

    -h, --help
            Print help information

    -i, --include tech <TECHS>
            Technology to be included, even if its not detected by wappalyzer. ( -i PHP,IIS )

    -J, --json
            Save the output as json

    -k, --config <CONFIG>
            Config file to use [default: ~/.config/chameleon/config.toml]

    -L, --hosts-file <HOSTS_FILE>
            List of hosts to scan

    -o, --output <OUTPUT>
            Save the output into a file

    -s, --ms <MATCHSIZE>...
            Match HTTP response size. Comma separated list of sizes

    -S, --fs <FILTERSIZE>...
            Filter HTTP response size. Comma separated list of sizes

    -t, --concurrency <CONCURRENCY>
            Number of concurrent threads ( default: 200 ) [default: 40]

    -T, --tech url <TECH_URL>
            URL which will be scanned for technologies. By default, this is the same as '-u',
            however it can be changed using '-T'

    -u, --url <URL>
            url to scan

    -U, --user-agent <USERAGENT>
            Change the value for the user-agent header [default: "Chameleon /
            https://github.com/iustin24/chameleon"]

    -V, --version
            Print version information

    -w, --wordlist <WORDLIST>
            Main wordlist to use for bruteforcing

    -W, --small-wordlist <SMALL_WORDLIST>
            Wordlist used to generate files by adding extensions ( FUZZ.%ext )

    -X, --methods <METHODS>...
            HTTP Methods to use. Comma separated list of sizes [default: GET]
```
