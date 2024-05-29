!!! info ""

    #### Basic Programming Operations

    |Operation|Code|
    |:-|:-|
    |Declare a variable|Dim myVar As String|
    |Set the value of a variable|myVar = “some value”|
    |Set the value of an object variable|Set myObj = Range(“B2:C3”)|
    |Gather user input|userInput = InputBox(“What’s your favorite color?”)|
    |Print a message to the screen|MsgBox(“You shall not pass!”)|
    |Execute a macro from within another macro|Call myMacro|
    |Use a built-in worksheet function in a macro|Application.WorksheetFunction.CountA(“A:A”)|
    |Comment out a line of code - note the apostrophe (‘)|‘VBA will ignore me!|


    #### Basic Operations on Data

    |Operation|Code|
    |:-|:-|
    |Addition|imFour = 2 + 2|
    |Subtraction|imZero = 2 - 2|
    |Multiplication|imAlsoFour&nbsp; = 2 * 2|
    |Division (uses “/” operator)|MsgBox(10 / 3) ‘returns 3.333333|
    |Integer Division (uses “\” operator)|MsgBox(10 \ 3) ‘returns 3|
    |Concatenation|helloWorld = “Hello” &amp; “world”|



    #### Working With Worksheets

    |Example Scenario|VBA Code|
    |:-|:-|
    |Activate a sheet by referencing its name|Sheets(“Sheet 1”).Activate|
    |Activate a sheet by referencing its index|Sheets(1).Activate|
    |Print the name of the active worksheet|MsgBox(ActiveSheet.Name)|
    |Add a new worksheet|Sheets.Add|
    |Add a new worksheet and specify its name|Sheets.Add.Name = “My New Sheet”|
    |Delete a worksheet|Sheets(“My New Sheet”).Delete|
    |Hide a worksheet|Sheets(2).visible = False|
    |Unhide a worksheet|Sheets(2).visible = True|
    |Loop through all sheets in a workbook|Dim ws As Worksheet <br> For Each ws In ActiveWorkbook.Worksheets&nbsp;<br> MsgBox (ws.Name) <br> Next ws|

    #### Working With Workbooks

    |Example Scenario|VBA Code|
    |:-|:-|
    |Activate a workbook by referencing its name|Workbooks(“My Workbook”).Activate|
    |Activate the first workbook that was opened, among all open workbooks|Workbooks(1).Activate|
    |Activate the last workbook that was opened, among all open workbooks|Workbooks(Workbooks.Count).Activate|
    |Print the name of the active workbook|MsgBox(ActiveWorkbook.Name)|
    |Print the name of this workbook (the one containing the VBA code)|MsgBox(ThisWorkbook.Name)|
    |Add a new workbook|Workbooks.Add|
    |Open a workbook|Workbooks.Open(“C:\My Workbook.xlsx”)|
    |Save a workbook|Workbooks(“My Workbook”).Save|
    |Close a workbook and save changes|Workbooks(“My Workbook”).Close SaveChanges:=True|
    |Close a workbook without saving changes|Workbooks(“My Workbook”).Close SaveChanges:=False|
    |Loop through all open workbooks|Dim wb As Workbook <br> For Each wb In Application.Workbooks <br> MsgBox (wb.Name) <br> Next wb|

    References
    - [zerotomastery](https://zerotomastery.io/cheatsheets/vba-cheat-sheet/)
    - [DFT Wiki](https://dft.wiki/?p=2120)
