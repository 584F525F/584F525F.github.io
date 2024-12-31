!!! info ""

    [FDsploit - github](https://github.com/chrispetrou/FDsploit)

    FDsploit can be used to discover and exploit Local/Remote File Inclusion and directory traversal vulnerabilities automatically. In case an LFI vulnerability is found, --lfishell option can be used to exploit it. For now, 3 different types of LFI shells are supported:

    simple: This type of shell allows user to read files easily without having to type the url everytime. Also it only provides the output of the file and not the whole html-source code of the page which makes it very useful.
    expect: This type of shell is a semi-interactive shell which allows user to execute commands through PHP's expect:// wrapper.
    input: This type of shell is a semi-interactive shell which also allows user to execute commands through PHP's php://input stream.

!!! Info ""

    [Venom - github](https://github.com/v3n0m-Scanner/V3n0M-Scanner)

    Docker Install
    
    [Venom Docker - github](https://github.com/v3n0m-Scanner/V3n0M-Scanner/blob/master/docker/README.md)

    ```bash
    docker pull vittring/venom:yggdrasil
    ```

!!! info ""

    [ronin-vulns - github](https://github.com/ronin-rb/ronin-vulns)

    Install - requires Ruby >= 3.0.0

    ```bash
    gem install ronin-vulns
    ```

    Gemfile

    ```bash
    gem 'ronin-vulns', '~> 0.1'
    ```

    gemspec

    ```bash
    gem.add_dependency 'ronin-vulns', '~> 0.1'
    ```
