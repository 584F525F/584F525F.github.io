!!! info ""

    Source: [Async-DirBuster](https://github.com/584F525F/Async-DirBuster)

    #### Requirements

    ```bash
    pip install aiohttp beautifulsoup4 termcolor
    ```

    #### Usage

    Basic usage

    ```python
    python directory_buster.py -u <target_url> -w <path_to_wordlist>
    ```

    Custom Header

    ```python
    python directory_buster.py -u https://example.com -w wordlist.txt -H 'Authorization: Bearer token'
    ```

    Extensions

    ```python
    python directory_buster.py -u https://example.com -w wordlist.txt -x php asp
    ```

    Saving results to the file

    ```python
    python directory_buster.py -u https://example.com -w wordlist.txt -o output.txt
    ```

    #### Supported flags

    |Flag|Description|
    |:-|:-|
    |-x | Specify a list of file extensions to append to the directories in the wordlist (e.g., x php asp)|
    |-r | Follow redirects. If this flag is set, the script will follow HTTP redirects (3xx tatus codes)|
    |-H | Specify custom HTTP headers in the format 'Header1: value1' 'Header2: value2'|
    |-a <user_agent> | Set a custom User-Agent string. The default is directorybuster/1.0|
    |-ht | Hide response title in output|
    |-m c <status_codes> | Include status codes to match, separated by space (e.g., -m c 200 04)|
    |-ms <response_sizes> | Match response sizes, separated by space|
    |-fc <status_codes> | Filter status codes, separated by space (default is filtering 404)|
    |-fs <response_sizes> | Filter response sizes, separated by space|
    |-o <output_file> | Path to the output file to save the result|

    #### Note

    - Matching and Filtering Response Length together is not available at the moment. Choose one of them in the command-line arguments.
    - Matching and Filtering Response Status Code together is not available at the moment. Choose one of them in the command-line arguments.
