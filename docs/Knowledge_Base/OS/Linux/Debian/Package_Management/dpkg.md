??? info "Using DPKG - LOW LEVEL - Dependency Issues (BE AWARE)"

??? info "List all installable packages in a directory"
    ### List all installable packages in a directory
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


??? "Finding package links for dpkg and using wget to download"
    
    Newer releases [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
    Older releases [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

    Check what release you have
    ```
    lsb_release -a
    ```