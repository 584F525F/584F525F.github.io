!!! danger ""
    
    BE AWARE!
    - DPKG is LOW LEVEL
    - You might encounter Dependency Issues

!!! info ""

    #### List all installable packages in a directory

    ```bash
    cd <DIR>
    sudo dpkg -l
    ```

!!! info ""

    #### To search for name you can use wild card for parts of name

    ```bash
    sudo dpkg -l <Install_Package_Name>*
    sudo dpkg -l *<Install_Package_Name>*
    ```

!!! info  ""

    #### To install a local package file

    ```bash
    <Path> dpkg -i ./* #THIS INSTALLS ALL PACKAGES IN THAT LOCATION
    <Path> dpkg -i <Install_Package_Name> #THIS INSTALLS 1 PACKAGE
    ```

!!! info  ""

    #### Check package info

    ```bash
    sudo dpkg --info <Package_Name>
    ```

!!! info  ""

    #### List file in an install package

    ```bash
    sudo dpkg --listfiles <Package_Name>
    ```

!!! info  ""

    #### Get package name for a dirctory

    ```bash
    dpkg --search <Path>    #Example  dpkg --search /opt/Adobe/Reader9/
    ```
    
!!! info  ""

    #### Uninstall package and remove all its files

    ```bash
    sudo dpkg --purge <Package_Name>
    ```
    
!!! info  ""

    #### Reconfiguring an installed package

    ```bash
    sudo dpkg-reconfigure <Package_Name>
    ```

!!! info  ""

    #### Finding package links for dpkg and using wget to download

    Newer releases [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
    Older releases [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

    Check what release you have

    ```bash
    lsb_release -a
    ```
