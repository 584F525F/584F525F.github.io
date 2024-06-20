!!! info ""

    ### Installing tree
    
    #### For Debian distros

    ```bash
    sudo apt install tree
    ```
    
    #### For Arch-based distros

    ```bash
    sudo pacman -S tree
    ```
    
    ### treeing a directory

    ```bash
    tree target_directory
    ```
    
!!! info ""

    ### Tree Commands

    #### List only directories

    Use the `-d` option to list only the directories, at a specified location

    ```bash
    tree -d target_directory
    ```
    
    #### List hidden files
        
    use the `-a` option to show hidden files

    ```bash
    tree -a target_directory
    ```
        
    #### Include the path of files

    Use the `-f` option to get the path for each file

    ```bash
    tree -f directory.
    ```

    But what about getting the full path? Well, you just have to append the full path of a directory (from home to the target one)

    ```bash
    tree -f /home/sagar/Directory
    ```

    Or you can use cd into the directory and then run the following

    ```bash
    tree -f "$(pwd)"
    ```

    #### List files and directories based on the level
        
    If the directory has hundreds of subdirectories and if you only want to list the first certain levels such as want to include the first one or two subdirectories.
    
    Use the `-L` option to specify the levels

    ```bash
    tree -L Level
    ```
    
    example, listing files that are at level 2

    ```bash
    tree -L 2
    ```
        
    #### List files with permission

    Use the `-p` option to list file permissions

    ```bash
    tree -p TargetDirectory
    ```
    
    for better readability use it with `-h` option, example

    ```bash
    tree -ph MUSIC
    ```
        
    #### Get the file size of a directory using the tree command
        
    The tree command can show you the size of each file and directory, at a specified location and will also sum the size for you n the end.

    ```bash
    tree -df -h TargetDirectory
    ```

    #### List files based on the last modification using the tree command
        
    There are two ways of sorting files based on modification:

    - First modified       
    - Last modified

    ##### Sort files based on first modification
    
    Use the `-c` option to sort files based on file modification, were modified the first by default
    Use the `-D` option to get the date and time of modification

    ```bash
    tree -cD TargetDirectory
    ```

    #### Sort files based on the last modification
    
    Use the `-c` option to list files based on the first modification
    Use the `-r` option which will reverse the effect of `-c` option

    ```bash
    tree -cDr TargetDirectory
    ```
