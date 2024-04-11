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

    #### create a folder in D:\Temp\ with name "Test Folder"

    ```powershell
    New-Item -Path 'D:\temp\Test Folder' -ItemType Directory
    ```

    #### 

    ```powershell

    ```

    #### 

    ```powershell

    ```

    #### 

    ```powershell

    ```

    #### 

    ```powershell

    ```

    #### 

    ```powershell

    ```

