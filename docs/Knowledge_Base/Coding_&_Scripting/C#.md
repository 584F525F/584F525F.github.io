!!! info ""

    ## Visual Studio - Windows Forms Embed Resources


    ### Creating a folder and Embedding a resource

    Create a Folder, this is the Folder that will contain our Embedded File

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-0.png)

    I named the Folder **Files**

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-1.png)

    You can now add a file to that Folder

    I added file **example_file.txt**

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-2.png)

    Right click the file > **Properties**

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-4.png)

    Change the **BuildAction** to **Embedded resource**

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-5.png)


    ### Creating the Visual Form

    I added a Button and a multiline TextBox. I also changed the names on both items so we know what I am calling.

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-8.png)

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-9.png)

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-3.png)


    ### The Code part

    #### The namespace

    On the Visual Form, double click the Button

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-6.png)

    At the of the page, add the following

    ```c#
    using System.IO;
    using System.Reflection;
    ```

    In the Button function, add the following code

    ```c#
    Assembly asm = Assembly.GetExecutingAssembly();
    string[] names = asm.GetManifestResourceNames();
    foreach (var name in names) { textBox_Embedded_File_Contents.Text = name + Environment.NewLine; }
    ```

    What we will use above code for is only to get the namespace call for the text file so we can use it in the next steps.

    So far this is what the code looks like

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-7.png)

    First run **F5**, Click the Button. Now we can see how the file is being called with the namespace. So it's doing <namespace>.<Folder_Name>.<File_Name>

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-10.png)

    #### Reading the file content

    Now that we know the namespace call for this file, we will remove that code section and replace it with the following

    ```c#
    Assembly asm = Assembly.GetExecutingAssembly();
    StreamReader reader = new StreamReader(asm.GetManifestResourceStream("Example.Files.example_file.txt")); //ConfigurationRepeater is the namespace of the project
    textBox_Embedded_File_Contents.Text = reader.ReadToEnd();
    ```

    This is what the code looks like now

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-11.png)

    Run the form again **F5**, Click the Button and it should read the Embedded File contents and print them to the TextBox.

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-12.png)

    It indeed printed the file contents correctly

    ![alt text](/Knowledge_Base/images/c-sharp-si87tgksb-13.png)
