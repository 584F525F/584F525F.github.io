!!! info ""

    ### Networking Refresher
   
    
    !!! info ""
    
        #### IP Addresses
    
    
    !!! info ""
    
        #### MAC Addresses
    
        [OUI Lookup](https://aruljohn.com/mac/90CDB6C5A2EF)

    
    !!! info ""
    
        #### TCP, UDP, and the Three-Way Handshake
    
        TCP (Transmission Control Protocol) and UDP (User Datagram Protocol)

        **TCP Handshake**:

        - **SYN (Synchronize)**: The initiating device (often referred to as the client) sends a TCP packet with the SYN flag set to the destination device (often referred to as the server). This packet indicates the desire to establish a connection and includes an initial sequence number.
        - **SYN-ACK (Synchronize-Acknowledge)**: Upon receiving the SYN packet, the destination device responds with a TCP packet that has both the SYN and ACK (acknowledge) flags set. This packet acknowledges the receipt of the initial SYN packet and also includes its own initial sequence number
        - **ACK (Acknowledge)**: Finally, the initiating device acknowledges the SYN-ACK packet by sending an ACK packet back to the destination. This packet confirms the establishment of the connection and typically contains an incremented sequence number.
    
    
    !!! info ""
    
        #### Common Ports and Protocols
    
        Here are some commonly used ports and the protocols associated with them in computer networking:

        |Protocol|Port|TCP/UDP|
        |:-|:-|:-|
        |FTP (File Transfer Protocol) | 21 | TCP|
        |SSH (Secure Shell) | 22 | TCP|
        |Telnet | 23 | TCP|
        |SMTP (Simple Mail Transfer Protocol) | 25 | TCP|
        |DNS (Domain Name System) | 53 | TCP & UDP|
        |HTTP (Hypertext Transfer Protocol) | 80 | TCP|
        |HTTPS (Hypertext Transfer Protocol Secure) | 443 | TCP|
        |DHCP (Dynamic Host Configuration Protocol) | 67 & 68 | UDP|
        |POP3 (Post Office Protocol version 3) | 110 | TCP|
        |IMAP (Internet Message Access Protocol) | 143 | TCP|
        |SNMP (Simple Network Management Protocol) | 161 | UDP|
        |RDP (Remote Desktop Protocol) | 3389 | TCP|
        |NTP (Network Time Protocol) | 123 | UDP|
        |SMB (Server Message Block) | 445 | TCP|
        |FTPS (FTP over SSL/TLS) | 990 | TCP|
        |TFTP (Trivial File Transfer Protocol) | 69 | UDP|
        |LDAP (Lightweight Directory Access Protocol) | 389 | TCP & UDP|
        |MySQL | 3306 | TCP|
        |RDP (Remote Desktop Protocol) | 3389 | TCP|
    
    
    !!! info ""
    
        #### The OSI Model
    
        |OSI Layer Number|OSI Layer Name|Description|
        |:-|:-|:-|
        |1|Physical Layer | The physical layer is responsible for the transmission and reception of raw unstructured data bits over a physical medium. It defines the electrical, mechanical, and functional characteristics of the physical interface between devices.|
        |2|Data Link Layer | The data link layer handles the reliable transmission of data frames between directly connected nodes over a physical link. It provides error detection and correction, flow control, and handles access to the physical medium. Ethernet, Wi-Fi, and PPP (Point-to-Point Protocol) are examples of data link layer protocols.|
        |3|Network Layer | The network layer enables the routing of data packets across different networks. It deals with logical addressing and determines the best path for data delivery based on network conditions and routing protocols. The IP (Internet Protocol) is a key network layer protocol.|
        |4|Transport Layer | The transport layer ensures the reliable and orderly delivery of data between end systems. It breaks data into smaller segments, manages end-to-end communication, and provides error recovery, flow control, and congestion control. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) operate at this layer.|
        |5|Session Layer | The session layer establishes, manages, and terminates communication sessions between applications. It provides synchronization and dialog control mechanisms to enable seamless communication between devices. This layer also handles session checkpointing and recovery.|
        |6|Presentation Layer | The presentation layer is responsible for data representation, encryption, compression, and formatting. It ensures that data sent by the application layer of one system is understandable by the application layer of another system. This layer deals with data syntax and semantics.|
        |7|Application Layer | The application layer is the closest layer to the end-user and provides services directly to user applications. It includes protocols for various application-level services such as file transfer, email, web browsing, and remote access. Examples of protocols at this layer include HTTP, SMTP, FTP, and DNS.|
    
    
    !!! info ""
    
        #### Subnetting

        **Resources**:

        - [Seven Second Subnetting](https://www.youtube.com/watch?v=ZxAwQB8TZsM)
        - [Subnet Guide](https://drive.google.com/file/d/1ETKH31-E7G-7ntEOlWGZcDZWuukmeHFe/view)

        **Summary:**

        Subnetting is the process of dividing a network into smaller subnetworks called subnets. It allows for more efficient use of IP addresses and facilitates network management and routing. Subnetting is commonly used in IPv4 networks.

        Subnetting involves borrowing bits from the host portion of an IP address to create a subnet identifier. By doing this, a network can be divided into multiple subnets, each with its own range of IP addresses.

        CIDR (Classless Inter-Domain Routing) notation is a method used to represent IP addresses and their corresponding subnet masks. It specifies the network prefix length, which indicates the number of bits used for the network portion of the IP address. CIDR notation is expressed by appending a forward slash (/) followed by the prefix length to the IP address.

        Here's an example to illustrate subnetting and CIDR notation:

        Consider an IP address: 192.168.0.0/24

        In this example, the IP address is in the format of "192.168.0.0" and the "/24" represents the prefix length, indicating that the first 24 bits represent the network portion of the IP address, while the remaining 8 bits represent the host portion.

        With a /24 prefix length, the subnet mask for this network would be 255.255.255.0. This means that the first three octets are reserved for the network, and the last octet can be used for addressing hosts within the subnet.

        To subnet this network further, additional bits can be borrowed from the host portion. For instance, if we borrow 2 bits, we can create 4 subnets. The subnet mask would become 255.255.255.192 (in binary: 11111111.11111111.11111111.11000000).

        The four resulting subnets would be:

        Subnet 1: 192.168.0.0/26 (network range: 192.168.0.0 - 192.168.0.63)
        Subnet 2: 192.168.0.64/26 (network range: 192.168.0.64 - 192.168.0.127)
        Subnet 3: 192.168.0.128/26 (network range: 192.168.0.128 - 192.168.0.191)
        Subnet 4: 192.168.0.192/26 (network range: 192.168.0.192 - 192.168.0.255)
        Each subnet can then be assigned to a different segment or used for different purposes within the network.

        CIDR notation provides a concise way to represent networks and subnets by specifying the prefix length. It allows for flexibility in defining network boundaries and enables efficient address allocation in IP networking.


        ![alt text](/Knowledge_Base/images/ETH-img-s768tgisg7-0.png)

        Bits

        ![alt text](/Knowledge_Base/images/ETH-img-s768tgisg7-2.png)


!!! info ""

    ### Setting Up Our Lab
    
    
    !!! info ""
    
        #### Installing VMWare / VirtualBox
    
        - [VMware](https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html)
        - [VirtualBox](https://www.virtualbox.org/wiki/Downloads)


    !!! info ""
    
        #### Configuring VirtualBox
    
    
    !!! info ""
    
        #### Installing Kali Linux
    
        - [Download Kali](https://www.kali.org/get-kali/#kali-virtual-machines)
        - [Download 7zip](https://www.7-zip.org/download.html)

        Kali 2019.4. The credentials of root:toor
        The credentials, as of 2020.1, are kali:kali


!!! info ""

    ### Introduction to Linux

    
    !!! info ""
    
        #### Exploring Kali Linux
    
    
    
    !!! info ""
    
        #### Sudo Overview
    
    
    
    !!! info ""
    
        #### Navigating the File System
    
    
        Here are explanations and examples of the commands mentioned in this video:

        |Command|Description|Example|
        |:-|:-|:-|
        |`pwd` (Print Working Directory) | Displays the current working directory | Running pwd in the terminal would show the absolute path of the current directory, such as "/home/user/documents".|
        |`cd` (Change Directory) | Allows you to change the current working directory | Running cd /home/user/documents would change the directory to "/home/user/documents".|
        |`cd ..` (Change to Parent Directory) | Moves up one level in the directory hierarchy | Running cd .. in "/home/user/documents" would move to the "/home/user" directory.|
        |`ls` (List Directory Contents) | Lists the files and directories in the current directory | Running ls would display the files and directories in the current directory.|
        |`ls -la` (List Detailed Directory Contents) | Lists detailed information about files and directories, including hidden files | Running ls -la would display a detailed list of files and directories, including hidden files, in the current directory.|
        |`mkdir` (Make Directory) | Creates a new directory | Running mkdir new_folder would create a new directory named "new_folder" in the current directory.|
        |`rmdir` (Remove Directory) | Removes an empty directory | Running rmdir empty_folder would remove the directory named "empty_folder" if it is empty.|
        |`man` (Manual) | Displays the manual pages for a specified command | Running man ls would show the manual pages with detailed information about the ls command.|
        |`echo` | Displays text or variables as output | Running echo "Hello, world!" would output "Hello, world!" in the terminal.|
        |`>` (Output Redirection) | Redirects the output of a command to a file and overwrites the file if it already exists | Running echo "Hello" > greeting.txt would write the text "Hello" to a file named "greeting.txt" or overwrite the file if it exists.|
        |`>>` (Append Output) | Redirects the output of a command and appends it to a file | Running echo "World!" >> greeting.txt would append the text "World!" to the end of the "greeting.txt" file.|
        |`rm` (Remove) | Deletes files or directories | Running rm file.txt would delete the file named "file.txt" from the current directory.|
        |`mv` (Move) | Moves or renames files and directories | Running mv file.txt new_directory/file_renamed.txt would move the file "file.txt" to the "new_directory" and rename it as "file_renamed.txt".|
        |`cp` (Copy) | Copies files and directories | Running cp file.txt backup/file_copy.txt would create a copy of "file.txt" named "file_copy.txt" in the "backup" directory.|
        |`locate` | Searches for files and directories in a prebuilt database | Running locate myfile.txt would search for the file named "myfile.txt" in the prebuilt database and display its path if found.|
        |`updatedb` | Updates the database used by the locate command to reflect recent changes in the file system | Running updatedb would update the database, allowing the locate command to provide up-to-date search results.|
        |`passwd` | Allows a user to change their password | Running passwd would prompt the user to enter their current password and then set a new password.|

        Remember to exercise caution when using commands like rm as they can permanently delete files. It's always a good practice to double-check before executing such commands.


    
    !!! info ""
    
        #### Users and Privileges
    
        In the ls -la output, the "rwx" refers to the permissions associated with a file or directory. The permissions are displayed for three different entities: the owner, the group, and other users. Each entity has three permission categories: read (r), write (w), and execute (x). Here's a breakdown of what each permission category represents:

        - Read (r): Allows the entity to read or view the contents of a file or the names of files within a directory.
        - Write (w): Enables the entity to modify or write to a file or add, delete, or rename files within a directory.
        - Execute (x): Grants the entity the permission to execute a file or enter a directory. For directories, execute permission is required to access its contents.

        In the `ls -la` output, the permissions are displayed as a series of nine characters. The first character represents the file type (e.g., `-` for a regular file, `d` for a directory). The next three characters represent the owner's permissions, followed by the group's permissions, and then the permissions for other users.

        !!! example ""
        
            For example, let's consider an `ls -la` output line:

            `-rwxr-x--- 1 user group 4096 May 10 12:34 myfile.txt`

            In this example, the permissions are broken down as follows:

            |part|Explanation|
            |:-|:-|
            |**`-rwxr-x---`** | The first character indicates that it is a regular file. The following three characters (rwx) represent the owner's permissions (read, write, and execute). The next three characters (**`r-x`**) represent the group's permissions (read and execute). The last three characters (*`---`*) represent the permissions for other users (no permissions).|
            | **`1`** | Indicates the number of hard links to the file.|
            | **`user`** | Refers to the owner of the file.|
            | **`group`** | Refers to the group assigned to the file.|
            | **`4096`** | Indicates the file size in bytes.|
            | **`May 10 12:34`** | Specifies the date and time of the last modification.|
            | **`myfile.txt`** | Represents the name of the file.|
        
            It's worth noting that if a permission is not granted for a particular entity, a hyphen (`-`) is displayed in its place. Additionally, the output can include additional information such as special permissions, ownership, and timestamps.

        Here are explanations and examples of the commands mentioned in this video. Please note, Teachable blocks the mention of some of the sensitive paths shown in the video, so we cannot display them in text format here:

        |Command|Explanation|Example|
        |:-|:-|:-|
        | **`chmod`** | (Change Mode) Changes the permissions of a file or directory. | Running `chmod +x script.sh` would add the execute permission to the file "script.sh", allowing it to be executed as a script.|
        | **`adduser`** | Creates a new user account. | Running adduser john would create a new user account with the username "john" and prompt for additional user information.|
        | **`su`** | (Switch User) Allows a user to switch to another user account. | Running su jane would switch to the user account "jane" after entering the password for that account.|
        | **`/etc/sudoers`** | Displays the content of the `/etc/sudoers` file, which contains configuration information for the sudo command. | Running **`/etc/sudoers`** would display the configuration directives for sudo access and permissions.|
        | **`sudo -l`** | Lists the commands a user is allowed to run with sudo privileges. | Running **`sudo -l`** would display the commands and permissions available to the current user with sudo access.|
        
        Please note that some of these commands require administrative privileges, and caution should be exercised when modifying system files or working with user accounts.
    
    !!! info ""
    
        #### Common Network Commands
    
        Here are explanations and examples of the commands mentioned in this video:

        |Command|Explanation|Example|
        |:-|:-|:-|
        | **`ip a`** | Displays the network interfaces and their associated IP addresses. | Running ip a would show information about network interfaces, including their IP addresses, MAC addresses, and other details.|
        | **`ifconfig`** | Displays the configuration and status of network interfaces. | Running ifconfig would show the configuration details, including IP addresses, MAC addresses, and other information for active network interfaces.|
        | **`iwconfig`** | Displays the configuration and status of wireless network interfaces. | Running iwconfig would show the configuration details, such as wireless signal strength, frequency, and encryption information, for active wireless interfaces.|
        | **`ip n`** | Displays the Neighbor Table, which contains the IP-to-MAC address mappings for devices in the local network. | Running ip n would show the IP and MAC addresses of devices that have recently communicated with the current device.|
        | **`arp -a`** | Displays the ARP (Address Resolution Protocol) cache, which maps IP addresses to MAC addresses. | Running arp -a would show the IP and MAC addresses of devices that have been resolved recently by the ARP protocol.|
        | **`ip r`** | Displays the routing table, which contains information about network routes. | Running ip r would show the routing table, including destination networks, gateway IP addresses, and network interfaces.|
        | **`route`** | Displays or manipulates the IP routing table. | Running route would display the routing table, similar to the ip r command.|
        | **`ping`** | Sends ICMP echo requests to a specified IP address to check network connectivity and measure round-trip time. | Running ping 8.8.8.8 would send ICMP echo requests to the IP address "8.8.8.8" (Google's DNS server) and display the round-trip time and packet loss statistics.|
        
        These commands are commonly used for network troubleshooting, configuration, and gathering network-related information in Linux systems.


    !!! info ""

        #### Viewing, Creating, and Editing Files

        Here are explanations and examples of the commands mentioned in this video:
        
        |Command|Explanation|Example|
        |:-|:-|:-|
        | **`echo "hello" > hey.txt`** | Creates a new file named "hey.txt" with the content "hello" and overwrites the file if it already exists. | Running `echo "hello" > hey.txt` would create a file named "hey.txt" and write the word "hello" into it.|
        |-|-|-|
        | **`echo "hello again" >> hey.txt`** | Appends the content "hello again" to an existing file named "hey.txt" or creates a new file if it doesn't exist. | Running `echo "hello again" >> hey.txt` would append the text "hello again" to the end of the "hey.txt" file.|
        | **`touch newfile.txt`** | Creates a new empty file named "newfile.txt" or updates the timestamp of an existing file to the current time. | Running `touch newfile.txt` would create an empty file named "newfile.txt" if it doesn't exist or update its timestamp if it already exists.|
        | **`nano newfile.txt`** | Opens the text editor Nano and allows you to create or edit the content of a file named "newfile.txt". | Running `nano newfile.txt` would open the Nano editor, where you can enter or modify text in the "newfile.txt" file.|
        | **`mousepad newfile.txt`** | Opens the Mousepad text editor and allows you to create or edit the content of a file named "newfile.txt". | Running `mousepad newfile.txt` would open the Mousepad editor, where you can enter or modify text in the "newfile.txt" file.|
            
        These commands are commonly used for file manipulation and editing in Linux systems. The echo command is used to print text or variables to the terminal or redirect them to files. The touch command is used to create or update file timestamps. The nano and mousepad commands are text editors that allow you to create and modify files directly from the terminal.
    
    
    !!! info ""
    
        #### Starting and Stopping Services
    
        Here are explanations and examples of the commands mentioned in this video:

        |Command|Explanation|Example|
        |:-|:-|:-|
        | **`sudo service apache2 start`** | Starts the Apache web server service. | Running `sudo service apache2 start` would initiate the Apache web server and make it available for serving web pages.|
        | **`sudo service apache2 stop`** | Stops the Apache web server service. | Running `sudo service apache2 stop` would halt the running Apache web server, shutting down any active web page serving.|
        | **`python3 -m http.server 80`** | Starts a simple HTTP server using Python on port 80. | Running `python3 -m http.server 80` would start a basic HTTP server on port 80, allowing you to serve files from the current directory.|
        | **`sudo systemctl enable ssh`** | Enables the SSH (Secure Shell) service to start automatically on system boot. | Running `sudo systemctl enable ssh` would configure the system to start the SSH service during system startup.|
        | **`sudo systemctl disable ssh`** | Disables the SSH service from starting automatically on system boot. | Running `sudo systemctl disable ssh` would prevent the SSH service from starting automatically during system startup.|
        
        These commands are frequently used in Linux systems for managing services, starting and stopping processes, and enabling or disabling specific services at system startup. The sudo command is used to execute commands with superuser privileges. The service and systemctl commands are used to manage system services.|
    
    !!! info ""
    
        #### Installing and Updating Tools
    
        Here are explanations and examples of the commands mentioned in this video:

        |Command|Explanation|Example|
        |:-|:-|:-|
        |**`sudo apt update && sudo apt upgrade`** | Updates the package lists and upgrades installed packages on a Debian-based Linux system using the APT package manager. | Running `sudo apt update && sudo apt upgrade` would update the package lists to retrieve information about available updates, and then upgrade the installed packages to their latest versions|
        |**`sudo apt install cron-daemon-common`** | Installs the "cron-daemon-common" package using APT. Cron is a time-based job scheduler in Linux systems, and the "cron-daemon-common" package provides common files and utilities for the cron daemon. | Running `sudo apt install cron-daemon-common` would download and install the "cron-daemon-common" package on the system|
        |**`sudo git clone https://github.com/Dewalt-arch/pimpmykali.git`** | Clones a Git repository from the specified URL using the Git version control system. | Running `sudo git clone https://github.com/Dewalt-arch/pimpmykali.git` would clone the repository from the given URL and create a local copy of the repository's files and version history|

        These commands are commonly used in Linux systems for updating packages, installing new software, and managing version-controlled repositories. The sudo command is used to execute commands with superuser privileges. The apt command is used for package management in Debian-based distributions. The git command is used for version control and working with Git repositories.
    
    !!! info ""
    
        #### Scripting with Bash

        ```bash
        #!/bin/bash
        if [ "$1" == "" ]
        then
        echo "You forgot an IP address!"
        echo "Syntax: ./ipsweep.sh 192.168.1"

        else
        for ip in `seq 1 254`; do
        ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
        done
        fi
        ```

        Question: My bash script is producing an error with “seq”. How do I resolve?

        Resolution: Ensure use of backtick (`) instead of using single quote ('). Alternatively, use $(seq 1 254) instead of seq


!!! info ""

    ### Introduction to Python
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### Strings
    
    

    
    !!! info ""
    
        #### Math
    
    

    
    !!! info ""
    
        #### Variables and Methods
    
    

    
    !!! info ""
    
        #### Functions
    
    

    
    !!! info ""
    
        #### Boolean Expressions and Relational Operators
    
    

    
    !!! info ""
    
        #### Conditional Statements
    
    

    
    !!! info ""
    
        #### Lists
    
    

    
    !!! info ""
    
        #### Tuples
    
    

    
    !!! info ""
    
        #### Looping
    
    

    
    !!! info ""
    
        #### Advanced Strings
    
    

    
    !!! info ""
    
        #### Dictionaries
    
    

    
    !!! info ""
    
        #### Importing Modules
    
    

    
    !!! info ""
    
        #### Sockets
    
    

    
    !!! info ""
    
        #### Building a Port Scanner
    
    

    
    !!! info ""
    
        #### User Input
    
    

    
    !!! info ""
    
        #### Reading and Writing Files
    
    

    
    !!! info ""
    
        #### Classes and Objects
    
    

    
    !!! info ""
    
        #### Building a Shoe Budget Tool
    
    

    




!!! info ""

    ### The Ethical Hacker Methodology
    
    

    
    !!! info ""
    
        #### The Five Stages of Ethical Hacking
    
    

    




!!! info ""

    ### Information Gathering (Reconnaissance)
    
    

    
    !!! info ""
    
        #### Passive Reconnaissance Overview
    
    

    
    !!! info ""
    
        #### Identifying Our Target
    
    

    
    !!! info ""
    
        #### Discovering Email Addresses
    
    

    
    !!! info ""
    
        #### Gathering Breached Credentials with Breach-Parse
    
    

    
    !!! info ""
    
        #### Hunting Breached Credentials with DeHashed
    
    

    
    !!! info ""
    
        #### Hunting Subdomains Part 1
    
    

    
    !!! info ""
    
        #### Hunting Subdomains Part 2
    
    

    
    !!! info ""
    
        #### Identifying Website Technologies
    
    

    
    !!! info ""
    
        #### Information Gathering with Burp Suite
    
    

    
    !!! info ""
    
        #### Google Fu
    
    

    
    !!! info ""
    
        #### Utilizing Social Media
    
    

    
    !!! info ""
    
        #### Additional Learning (OSINT Fundamentals)
    
    

    



!!! info ""

    ### Scanning & Enumeration
    
    

    
    !!! info ""
    
        #### Installing Kioptrix
    
    

    
    !!! info ""
    
        #### Scanning with Nmap
    
    

    
    !!! info ""
    
        #### Enumerating HTTP and HTTPS Part 1
    
    

    
    !!! info ""
    
        #### Enumerating HTTP and HTTPS Part 2
    
    

    
    !!! info ""
    
        #### Enumerating SMB
    
    

    
    !!! info ""
    
        #### Enumerating SSH
    
    

    
    !!! info ""
    
        #### Researching Potential Vulnerabilities
    
    

    
    !!! info ""
    
        #### Our Notes So Far
    
    

    



!!! info ""

    

    
    !!! info ""
    
        #### Vulnerability Scanning with Nessus
    
    

    
    !!! info ""
    
        #### Scanning with Nessus Part 1
    
    

    
    !!! info ""
    
        #### Scanning with Nessus Part 2
    
    

    



!!! info ""

    ### Exploitation Basics
    
    

    
    !!! info ""
    
        #### Reverse Shells vs Bind Shells
    
    

    
    !!! info ""
    
        #### Staged vs Non-Staged Payloads
    
    

    
    !!! info ""
    
        #### Gaining Root with Metasploit
    
    

    
    !!! info ""
    
        #### Manual Exploitation
    


    
    

    
    !!! info ""
    
        #### Brute Force Attacks
    
    
    
    !!! info ""
    
        #### Credential Stuffing and Password Spraying
    



    !!! info ""
    
        #### Our Notes, Revisited








!!! info ""

    ### New Capstone
    
    
    !!! info ""
    
        #### Introduction
    



    !!! info ""
    
        #### Set Up - Blue
    



    !!! info ""
    
        #### Walkthrough - Blue
    



    !!! info ""
    
        #### Set Up - Academy
    



    !!! info ""
    
        #### Walkthrough - Academy
    


    !!! info ""
    
        #### Walkthrough - Dev
    



    !!! info ""
    
    #### Walkthrough - Butler
    



    !!! info ""
    
        #### Walkthrough - Blackpearl
    

    
    !!! info ""
    
        #### Active Directory Overview
    




    !!! info ""
    
        #### Active Directory Overview
    
    
    
    
    
    !!! info ""
    
        #### Physical Active Directory Components
    
    
    
    
    
    
    !!! info ""
    
        #### Logical Active Directory Components
    
    
    
    
    
    




!!! info ""

    ### Active Directory Lab Build
    
    
    
    !!! info ""
    
        #### Lab Overview and Requirements
    
    
    
    
    
    !!! info ""
    
        #### Lab Build - (Cloud Alternative)
    
    
    
    
    
    !!! info ""
    
        #### Downloading Necessary ISOs
    
    

    
    !!! info ""
    
        #### Setting Up the Domain Controller
    
    

    
    !!! info ""
    
        #### Setting Up the User Machines
    
    

    
    !!! info ""
    
        #### Setting Up Users, Groups, and Policies
    
    

    
    !!! info ""
    
        #### Joining Our Machines to the Domain
    

    
    !!! info ""
    
        #### Attacking Active Directory: Initial Attack Vectors
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### LLMNR Poisoning Overview
    
    

    
    !!! info ""
    
        #### Capturing Hashes with Responder
    
    

    
    !!! info ""
    
        #### Cracking Our Captured Hashes
    
    

    
    !!! info ""
    
        #### LLMNR Poisoning Mitigation
    
    

    
    !!! info ""
    
        #### SMB Relay Attacks Overview
    
    

    
    !!! info ""
    
        #### SMB Relay Attacks Lab
    
    

    
    !!! info ""
    
        #### SMB Relay Attack Defenses
    
    

    
    !!! info ""
    
        #### Gaining Shell Access
    
    

    
    !!! info ""
    
        #### IPv6 Attacks Overview
    
    

    
    !!! info ""
    
        #### IPv6 DNS Takeover via mitm6
    
    

    
    !!! info ""
    
        #### IPv6 Attack Defenses
    
    

    
    !!! info ""
    
        #### Passback Attacks
    
    

    
    !!! info ""
    
        #### Initial Internal Attack Strategy
    
    

    




!!! info ""

    ### Attacking Active Directory: Post-Compromise Enumeration
    


    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### Domain Enumeration with ldapdomaindump
    
    

    
    !!! info ""
    
        #### Domain Enumeration with Bloodhound
    
    

    
    !!! info ""
    
        #### Domain Enumeration with Plumhound
    
    

    
    !!! info ""
    
        #### Domain Enumeration with PingCastle
    
    

    




!!! info ""

    ### Attacking Active Directory: Post-Compromise Attacks
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### Pass Attacks Overview
    
    

    
    !!! info ""
    
        #### Pass Attacks
    
    

    
    !!! info ""
    
        #### Dumping and Cracking Hashes
    
    

    
    !!! info ""
    
        #### Pass Attack Mitigations
    
    

    
    !!! info ""
    
        #### Kerberoasting Overview
    
    

    
    !!! info ""
    
        #### Kerberoasting Walkthrough
    
    

    
    !!! info ""
    
        #### Kerberoasting Mitigation
    
    

    
    !!! info ""
    
        #### Token Impersonation Overview
    
    

    
    !!! info ""
    
        #### Token Impersonation Walkthrough
    
    

    
    !!! info ""
    
        #### Token Impersonation Mitigation
    
    

    
    !!! info ""
    
        #### LNK File Attacks
    
    

    
    !!! info ""
    
        #### GPP / cPassword Attacks and Mitigations
    
    

    
    !!! info ""
    
        #### Mimikatz Overview
    
    

    
    !!! info ""
    
        #### Credential Dumping with Mimikatz
    
    

    
    !!! info ""
    
        #### Post-Compromise Attack Strategy
    
    

    




!!! info ""

    ### We've Compromised the Domain - Now What?
    
    

    
    !!! info ""
    
        #### Post-Domain Compromise Attack Strategy
    
    

    
    !!! info ""
    
        #### Dumping the NTDS.dit
    
    

    
    !!! info ""
    
        #### Golden Ticket Attacks Overview
    
    

    
    !!! info ""
    
        #### Golden Ticket Attacks
    

    
    !!! info ""
    
        #### Additional Active Directory Attacks
    
    

    
    !!! info ""
    
        #### Section Overview
    
    

    
    !!! info ""
    
        #### Abusing ZeroLogon
    
    

    
    !!! info ""
    
        #### PrintNightmare (CVE-2021-1675) Walkthrough
    
    

    



!!! info ""

    ### Active Directory Case Studies
    
    

    
    !!! info ""
    
        #### AD Case Study #1
    
    

    
    !!! info ""
    
        #### AD Case Study #2
    
    

    
    !!! info ""
    
        #### AD Case Study #3
    

    
    !!! info ""
    
        #### Post Exploitation
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### File Transfers Review
    
    

    
    !!! info ""
    
        #### Maintaining Access Overview
    
    

    
    !!! info ""
    
        #### Pivoting Overview
    
    

    
    !!! info ""
    
        #### Pivoting Walkthrough
    
    

    
    !!! info ""
    
        #### Cleaning Up
    
    

    



!!! info ""

    ### Web Application Enumeration, Revisited
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### Installing Go
    
    

    
    !!! info ""
    
        #### Finding Subdomains with Assetfinder
    
    

    
    !!! info ""
    
        #### Finding Subdomains with Amass
    
    

    
    !!! info ""
    
        #### Finding Alive Domains with Httprobe
    
    

    
    !!! info ""
    
        #### Screenshotting Websites with GoWitness
    
    

    
    !!! info ""
    
        #### Automating the Enumeration Process
    
    

    
    !!! info ""
    
        #### Additional Resources
    
    

    



!!! info ""

    ### Find & Exploit Common Web Vulnerabilities
    
    

    
    !!! info ""
    
        #### Introduction
    
    

    
    !!! info ""
    
        #### Lab Setup (full text instructions included in course notes)
    
    

    
    !!! info ""
    
        #### SQL Injection - Introduction
    
    

    
    !!! info ""
    
        #### SQL Injection - UNION
    
    

    
    !!! info ""
    
        #### SQL Injection - Blind Part 1
    
    

    
    !!! info ""
    
        #### SQL Injection - Blind Part 2
    
    

    
    !!! info ""
    
        #### SQL Injection - Challenge Waklthrough
    
    

    
    !!! info ""
    
        #### XSS - Introduction
    
    

    
    !!! info ""
    
        #### XSS - DOM Lab
    
    

    
    !!! info ""
    
        #### XSS - Stored Lab
    
    

    
    !!! info ""
    
        #### XSS - Challenge Walkthrough
    
    

    
    !!! info ""
    
        #### Command Injection - Introduction
    
    

    
    !!! info ""
    
        #### Command Injection - Basics
    
    

    
    !!! info ""
    
        #### Command Injection - Blind / Out-of-Band
    
    

    
    !!! info ""
    
        #### Command Injection - Challenge Walkthrough
    
    

    
    !!! info ""
    
        #### Insecure File Upload - Introduction
    
    

    
    !!! info ""
    
        #### Insecure File Upload - Basic Bypass
    
    

    
    !!! info ""
    
        #### Insecure File Upload - Magic Bytes
    
    

    
    !!! info ""
    
        #### Insecure File Upload - Challenge Walkthrough
    
    

    
    !!! info ""
    
        #### Attacking Authentication - Intro
    
    

    
    !!! info ""
    
        #### Attacking Authentication - Brute Force
    
    

    
    !!! info ""
    
        #### Attacking Authentication - MFA
    
    

    
    !!! info ""
    
        #### Attacking Authentication - Challenge Walkthrough
    
    


    
    !!! info ""
    
        #### XXE - External Entities Injection
    
    


    
    !!! info ""
    
        #### IDOR - Insecure Direct Object Reference
    
    


    
    !!! info ""
    
        #### Capstone - Introduction
    
    


    
    !!! info ""
    
        #### Capstone - Solution
    
    


    



!!! info ""

    ### Wireless Penetration Testing
    
    


    
    !!! info ""
    
        #### 001_Wireless_Penetration_Testing_Overview
    
    


    
    !!! info ""
    
        #### 002_WPA_PS2_Exploit_Walkthrough
    
    


    



!!! info ""

    ### Legal Documents and Report Writing
    


    !!! info ""
    
        #### 001_Common_Legal_Documents
    





    !!! info ""
    
        #### 002_Pentest_Report_Writing
    





    !!! info ""
    
        #### 003_Reviewing_a_Real_Pentest_Report
    







!!! info ""

    ### Career Advice
    