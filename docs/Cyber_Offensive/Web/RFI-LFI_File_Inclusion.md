[FDsploit](https://github.com/chrispetrou/FDsploit)

FDsploit can be used to discover and exploit Local/Remote File Inclusion and directory traversal vulnerabilities automatically. In case an LFI vulnerability is found, --lfishell option can be used to exploit it. For now, 3 different types of LFI shells are supported:

simple: This type of shell allows user to read files easily without having to type the url everytime. Also it only provides the output of the file and not the whole html-source code of the page which makes it very useful.
expect: This type of shell is a semi-interactive shell which allows user to execute commands through PHP's expect:// wrapper.
input: This type of shell is a semi-interactive shell which also allows user to execute commands through PHP's php://input stream.

