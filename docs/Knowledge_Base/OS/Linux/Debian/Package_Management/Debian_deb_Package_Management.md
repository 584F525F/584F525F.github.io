!!! "Using APT - Advanced Package Tool"
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
    
!!! "Adding Apt Repository In Ubuntu"
    Resources [How-to-add-apt-repository-in-ubuntu](https://linuxize.com/post/how-to-add-apt-repository-in-ubuntu/)

        
!!! "Adding Kali Repository to Ubuntu"

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

!!! "Using DPKG - LOW LEVEL - Dependency Issues (BE AWARE)"

    #List all installable packages in a directory
    ```
    cd <DIR>
    sudo dpkg -l
    ```

    #To search for name you can use wild card for parts of name
    ```
    sudo dpkg -l <Install_Package_Name>*
    sudo dpkg -l *<Install_Package_Name>*
    ```

    #To install a local package file
    ```
    <Path> dpkg -i ./* #THIS INSTALLS ALL PACKAGES IN THAT LOCATION
    <Path> dpkg -i <Install_Package_Name> #THIS INSTALLS 1 PACKAGE
    ```

    #Check package info
    ```
    sudo dpkg --info <Package_Name>
    ```

    #List file in an install package
    ```
    sudo dpkg --listfiles <Package_Name>
    ```

    #Get package name for a dirctory
    ```
    dpkg --search <Path>    #Example  dpkg --search /opt/Adobe/Reader9/
    ```
    
    #Uninstall package and remove all its files
    ```
    sudo dpkg --purge <Package_Name>
    ```
    
    #Reconfiguring an installed package
    ```
    sudo dpkg-reconfigure <Package_Name>
    ```


!!! "Finding package links for dpkg and using wget to download"
    
    Newer releases [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
    Older releases [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

    Check what release you have
    ```
    lsb_release -a
    ```

- SNAP [ubuntuhandbook](https://ubuntuhandbook.org/index.php/2021/01/earch-install-remove-snap-apps-command-line/)
- PIP - PYTHON    
- GIT
