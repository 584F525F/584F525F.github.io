!!! info ""

    ### Files

    #### Renaming files [replacing spcific chars in files]

    rename files, replacing any -opendir with nothing

    ```powershell
    get-childitem * -r | foreach {rename-item $_ $_.name.replace("-opendir","")}
    ```

    #### Get file full path

    Get full file path recursively from a directory, where the file extension is .md

    ```powershell
    get-childitem "C:\temp\test_folder" -recurse | where {$_.extension -eq ".md"} | % {Write-Host $_.FullName}
    ```

    another way of doing it

    ```powershell
    Get-ChildItem "C:\Users\yshana534\gibt\docs\Knowledge_Base" *.md -Recurse | Select-Object FullName
    ```

    #### Create a file

    create a file in D:\Temp\Test Folder with name "Test File.txt"

    ```powershell
    New-Item -Path 'D:\temp\Test Folder\Test File.txt' -ItemType File
    ```

    #### Check file existence

    check if file test.txt exists in 'D:\temp\test directory'

    ```powershell
    Test-Path D:\temp\test\test.txt
    ```

    #### Retrieving Item

    reading a file's content 'D:\Temp\Test\Test.txt'

    ```powershell
    Get-Content D:\temp\Test\test.txt
    ```

    #### Renaming a file

    rename file test.txt to test1.txt

    ```powershell
    Rename-Item D:\temp\Test\test.txt test1.txt
    ```

    #### Moving a file

    move a file from one directory to another 'D:\Temp\Test\Test.txt' to 'D:\Temp\Test1'

    ```powershell
    Move-Item D:\temp\Test\Test.txt D:\temp\Test1
    ```

    #### Deleting file(s)

    === "single file deletion"

        delete file 'D:\temp\Test Folder\test.txt'

        ```powershell
        Remove-Item 'D:\temp\Test Folder\test.txt'
        ```

    === "recursively deleting files"
        
        Delete all files in directory 'D:\temp\Test Folder'

        ```powershell
        Remove-Item 'D:\temp\Test Folder' -Recurse
        ```

    #### Copying file(s)

    === "copying a single file"
        delete file 'D:\temp\Test Folder\test.txt'
        ```powershell
        Copy-Item 'D:\temp\Test Folder\Test File.txt' 'D:\temp\Test Folder1\Test File1.txt'
        ```
    === "copying multiple files"
        
        Copy files from 1 directory to another
        ```powershell
        Copy-Item -Filter *.txt -Path 'D:\temp\Test Folder' -Recurse -Destination 'D:\temp\Test Folder1'
        ```

!!! info ""

    ### Folders

    #### create a folder
    
    create a folder in D:\Temp\ with name "Test Folder"

    ```powershell
    New-Item -Path 'D:\temp\Test Folder' -ItemType Directory
    ```

    #### Copying a folder

    === "copying a single folder"

        copy a single folder D:\Temp\Test Folder as D:\Temp\Test Folder1

        ```powershell
        Copy-Item 'D:\temp\Test Folder' 'D:\temp\Test Folder1'
        ```

    === "copying multiple folders"
        
        copy a folder recursively D:\Temp\Test Folder to D:\Temp\Test Folder1

        ```powershell
        Copy-Item 'D:\temp\Test Folder' -Destination 'D:\temp\Test Folder1'
        ```

    #### Renaming a folder

    renaming a folder D:\Temp\Test to D:\Temp\Test1

    ```powershell
    Rename-Item "D:\temp\Test Test1"
    ```

    #### moving a folder

    move a folder D:\Temp\Test to D:\Temp\Test1

    ```powershell
    Move-Item D:\temp\Test D:\temp\Test1
    ```

    #### Deleting a folder

    === "delete a single file"

        delete a folder D:\Temp\Test Folder1

        ```powershell
        Remove-Item 'D:\temp\Test Folder1'
        ```

    === "delete multiple files"
        
        deleting folders recursively in a directory D:\Temp\Test Folder1

        ```powershell
        Remove-Item 'D:\temp\Test Folder' -Recurse
        ```

    #### Check folder existence

    Check if path exists 'D:\temp\test'

    ```powershell
    Test-Path D:\temp\test
    ```
