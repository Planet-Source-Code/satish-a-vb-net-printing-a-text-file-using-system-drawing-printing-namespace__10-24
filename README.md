<div align="center">

## VB\.NET Printing a Text File \(Using System\.Drawing\.Printing Namespace\)


</div>

### Description

The code demonstrates how to work with System.Drawing.Printing Namespace
 
### More Info
 
Text File

knowledge in .NET Technologies

----

1. Add a module to your WindowsApplication Project

2. Paste the Code

3. Set Startup object as Main()

4. Run You have the output

Prints the Text File


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Satish A](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/satish-a.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__10-1.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/satish-a-vb-net-printing-a-text-file-using-system-drawing-printing-namespace__10-24/archive/master.zip)





### Source Code

```
Imports System.IO
Imports System.Drawing
Imports System.Drawing.Printing
Module Module1
 'Create objects
 Private WithEvents MyDoc As PrintDocument
 Private MyFile As StreamReader
 Sub Main()
  'Open a File
  MyFile = File.OpenText("c:\a.txt")
  MyDoc = New PrintDocument()
  MyDoc.Print()
 End Sub
 Private Sub OnPagePrint(ByVal Sender As Object, ByVal arg As System.Drawing.Printing.PrintPageEventArgs) Handles MyDoc.PrintPage
  'Event Fires at every Page has been printed
  Dim sngCurY As Single
  Dim sngLineHeight As Single
  Dim oFont As Font
  oFont = New System.Drawing.Font("Arial", 12)
  sngLineHeight = oFont.GetHeight(arg.Graphics)
  sngCurY = arg.MarginBounds.Top
  If MyFile.Peek() <> -1 Then
   Do
    sngCurY += sngLineHeight
    arg.Graphics.DrawString(MyFile.ReadLine(), oFont, Brushes.Black, arg.MarginBounds.Left, sngCurY)
   Loop Until sngCurY >= arg.MarginBounds.Bottom Or MyFile.Peek() = 1
  End If
  If MyFile.Peek <> -1 Then
   arg.HasMorePages = True
  Else
   arg.HasMorePages = False
  End If
 End Sub
End Module
```

