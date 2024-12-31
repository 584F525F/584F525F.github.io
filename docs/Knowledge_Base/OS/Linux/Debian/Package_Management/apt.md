!!! info ""
    
    #### Using APT - Advanced Package Tool
    
    [apt-get man pages](https://manpages.ubuntu.com/manpages/bionic/man8/apt-get.8.html)

    ##### Installing a package
	
    ```bash
    sudo apt-get install <PackageName>
    ```

    ##### Removing a package
	
    Removes a package, however it **leaves its configuration files on the system**

    ```bash
    sudo apt-get remove <PackageName>
    ```

    ##### Purging a package
	
    Removes the package and any of its configuration files as long as they are located in `/etc`.
    If you have configuration files in a location such as `/home` those configurations will remain there when using purge.

    ```bash
    sudo apt-get purge <PackageName>
    ```

    ##### Remove & Purging a package

    ```bash
    apt-get remove --purge packagename
    ```

    You can read more about the differences between purge and remove here [apt remove vs apt purge](https://itsfoss.com/apt-remove-purge/)

    ##### Upgrade OS run
	
    ```bash
    do-release-upgrade
    ```
    
    ##### To upgrade existing package
    
    ```bash
    sudo apt-get --only-upgrade install <PackageName>
    ```

    ##### To install & Remove a package
    
    ```bash
    sudo apt-get install <PackageName>
    sudo apt-get remove <PackageName>
    ```

    ##### To search for package
    
    ```bash
    apt search <PackageName>
    ```

    ##### See list of upgradable packages
    
    ```bash
    sudo apt-get update
    sudo apt list --upgradable
    ```

    ##### List installed packages
    
    ```bash
    sudo apt list --installed
    ```
    
    ###### View package details, version, etc.
    
    ```bash
    apt show <PackageName>
    ```

    ##### Check stats on installed Packages
    
    ```bash
    apt-cache stats
    ```

    ##### Show installed packages names
    
    ```bash
    apt-cache pkgnames
    apt-cache pkgnames <name>*
    ```

    ##### Search for package
    
    ```bash
    apt-cache search <name>
    ```

    ##### Check unmet dependencies
    
    ```bash
    apt-cache unmet
    ```

    ##### Check Install repos
    
    ```bash
    less /etc/apt/sources.list
    ```

    ##### apt manual pages
    
    ```bash
    man apt
    man apt-get
    ```

    ##### Packages installed with apt-get are located in /var/cache/apt/archives
    
    ##### To check Repo sources
    
    ```bash
    sudo apt edit-sources
    ```
    
!!! example ""
    
    #### Adding Apt Repository In Ubuntu
    Resources [How-to-add-apt-repository-in-ubuntu](https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/)

        
!!! example ""
    
    #### Adding Kali Repository to Ubuntu
	
    ##### Step-1: Install Git
	
    ```bash
    sudo apt install git
	git --version
	```
	
	##### Step-2: Install Python 2.7
	
    ```bash
    sudo apt install python2    <OR>     sudo apt install python-minimal
	python2 --version
	```
	
	##### Step-3: Install Katoolin
	
    ```bash
    cd ~
	sudo git clone <https://github.com/LionSec/katoolin.git>
	ls -l
	sudo cp katoolin/katoolin.py /usr/bin/katoolin
    ```
	
    Make the script executable
	
    ```bash
    sudo chmod +x /usr/bin/katoolin
	```
	
	##### Step-4: Launch Katoolin
	
    ```bash
    sudo katoolin
    ```

    OR
	
    ```bash
    sudo python2 /usr/bin/katoolin
    ```	
	
	##### Step-5: Add Kali Repositories & Update
	katoolin
	- Choose 1 "add Kali Linux repositories"
	- Choose 1 again "Add Kali Linux repositories"
	
	If you get the error gpg: keyserver receive failed: No name
	
    ```bash
    wget -q -O - archive.kali.org/archive-key.asc | sudo  apt-key add
	sudo apt update
    ```
	
	katoolin - Update repos

    ```bash
	- Option 1 "Add Kali Linux repositories"
	- Option 2 "Update"
	- When done, type gohome to return the katoolin main interface window.
	```
	
	##### Step-6: katoolin - View Categories to install Kali Linux Apps on Ubuntu

	```bash
    - Option 2 "View Categories"
	```
	
	##### Step-7: katoolin - Install the Classic Menu indicator

	```bash
    - Option 3 to Classic Menu indicator
	```
	
	##### Step-8: katoolin - Install Kali Menu

	```bash
    - Option 4 install the Kali menu
    ```
