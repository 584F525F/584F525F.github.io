??? "Using APT - Advanced Package Tool"
    #### Upgrade OS run
	```
    do-release-upgrade
    ```
    
    #### To upgrade existing package
    ```
    sudo apt-get --only-upgrade install <Package>
    ```

    #### To install & Remove a package
    ```
    sudo apt-get install <Package>
    sudo apt-get remove <Package>
    ```

    #### To search for package
    ```
    apt search <package>
    ```

    #### See list of upgradable packages
    ```
    sudo apt-get update
    sudo apt list --upgradable
    ```

    #### List installed packages
    ```
    sudo apt list --installed
    ```
    
    ##### View package details, version, etc.
    ```
    apt show <Package>
    ```

    #### Check stats on installed Packages
    ```
    apt-cache stats
    ```

    #### Show installed packages names
    ```
    apt-cache pkgnames
    apt-cache pkgnames <name>*
    ```

    #### Search for package
    ```
    apt-cache search <name>
    ```

    #### Check unmet dependencies
    ```
    aptcache unmet
    ```

    #### Check Install repos
    ```
    less /etc/apt/sources.list
    ```

    #### apt manual pages
    ```
    man apt
    man apt-get
    ```

    #### Packages installed with apt-get are located in /var/cache/apt/archives
    
    #### To check Repo sources
    ```
    sudo apt edit-sources
    ```
    
??? "Adding Apt Repository In Ubuntu"
    Resources [How-to-add-apt-repository-in-ubuntu](https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/)

        
??? "Adding Kali Repository to Ubuntu"

	#### Step-1: Install Git
	```
    sudo apt install git
	git --version
	```
	
	#### Step-2: Install Python 2.7
	```
    sudo apt install python2    <OR>     sudo apt install python-minimal
	python2 --version
	```
	
	#### Step-3: Install Katoolin
	```
    cd ~
	sudo git clone <https://github.com/LionSec/katoolin.git>
	ls -l
	sudo cp katoolin/katoolin.py /usr/bin/katoolin
    ```
	Make the script executable
	```
    sudo chmod +x /usr/bin/katoolin
	```
	
	#### Step-4: Launch Katoolin
	```
    sudo katoolin
    <OR>
	sudo python2 /usr/bin/katoolin
    ```	
	
	#### Step-5: Add Kali Repositories & Update
	katoolin
	- Choose 1 "add Kali Linux repositories"
	- Choose 1 again "Add Kali Linux repositories"
	
	If you get the error gpg: keyserver receive failed: No name
	```
    wget -q -O - archive.kali.org/archive-key.asc | sudo  apt-key add
	sudo apt update
    ```
	
	Update repos
	katoolin
    ```
	- Option 1 "Add Kali Linux repositories"
	- Option 2 "Update"
	- When done, type gohome to return the katoolin main interface window.
	```
	
	#### Step-6: View Categories to install Kali Linux Apps on Ubuntu
	katoolin
	```
    - Option 2 "View Categories"
	```
	
	#### Step-7: Install the Classic Menu indicator
	katoolin
	```
    - Option 3 to Classic Menu indicator
	```
	
	#### Step-8: Install Kali Menu
	katoolin
	```
    - Option 4 install the Kali menu
    ```


