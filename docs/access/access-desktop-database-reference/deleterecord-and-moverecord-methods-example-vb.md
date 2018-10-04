﻿---
title: DeleteRecord and MoveRecord Methods Example (VB)
TOCTitle: DeleteRecord and MoveRecord Methods Example (VB)
ms:assetid: f982368b-8828-3e29-9435-6c5cf44941bf
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250268(v=office.15)
ms:contentKeyID: 48548815
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DeleteRecord and MoveRecord Methods Example (VB)


**Applies to**: Access 2013 | Office 2013

This example demonstrates how to copy, move, edit, and delete the contents of a text file published to a Web folder. Other properties and methods used include [GetChildren](getchildren-method-ado.md), [ParentURL](parenturl-property-ado.md), [Source](source-property-ado-record.md), and [Flush](flush-method-ado.md).

``` 
 
'BeginDeleteRecordVB 
 
'Note: 
' IIS must be running for this sample to work. To 
' use this sample you must: 
' 
' 1. create folders named "test" and "test2" 
' in the root web folder of https://MyServer 
' 
' 2. Create a text file named "test2.txt" in the 
' "test" folder. 
' 3. Replace "MyServer" with the appropriate web 
' server name. 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 ' connection and recordset variables 
 Dim rsDestFolder As ADODB.Recordset 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 
 ' file as record variables 
 Dim rcFile As ADODB.Record 
 Dim rcDestFile As ADODB.Record 
 Dim rcDestFolder As ADODB.Record 
 Dim objStream As Stream 
 
 ' file variables 
 Dim strFile As String 
 Dim strDestFile As String 
 Dim strDestFolder As String 
 
 ' instantiate variables 
 Set rsDestFolder = New ADODB.Recordset 
 Set rcDestFolder = New ADODB.Record 
 Set rcFile = New ADODB.Record 
 Set rcDestFile = New ADODB.Record 
 Set objStream = New ADODB.Stream 
 
 ' open a record on a text file 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "url=https://MyServer/" 
 Cnxn.Open strCnxn 
 strFile = "test/test2.txt" 
 rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection 
 Debug.Print Cnxn 
 
 ' edit the contents of the text file 
 objStream.Open rcFile, , adOpenStreamFromRecord 
 
 Debug.Print "Source: " & strCnxn & rcFile.Source 
 Debug.Print "Original text: " & objStream.ReadText 
 
 objStream.Position = 0 
 objStream.WriteText "Newer Text. " 
 objStream.Position = 0 
 
 Debug.Print "New text: " & objStream.ReadText 
 
 ' reset the stream object 
 objStream.Flush 
 objStream.Close 
 rcFile.Close 
 
 ' reopen record to see new contents of text file 
 rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection 
 objStream.Open rcFile, adModeReadWrite, adOpenStreamFromRecord 
 
 Debug.Print "Source: " & strCnxn & rcFile.Source 
 Debug.Print "Edited text: " & objStream.ReadText 
 
 ' copy the file to another folder 
 strDestFile = "test2/test1.txt" 
 rcFile.CopyRecord "", "https://MyServer/" & strDestFile, "", "", adCopyOverWrite 
 
 ' delete the original file 
 rcFile.DeleteRecord 
 
 ' move the file from the subfolder back to original location 
 strDestFolder = "test2/" 
 rcDestFolder.Open strDestFolder, Cnxn ', adOpenIfExists 'Or adCreateCollection 
 Set rsDestFolder = rcDestFolder.GetChildren 
 rsDestFolder.MoveFirst 
 
 ' position current record at on the correct file 
 Do While Not (rsDestFolder.EOF Or rsDestFolder(0) = "test1.txt") 
 rsDestFolder.MoveNext 
 Loop 
 
 ' open a record on the correct row of the recordset 
 rcDestFile.Open rsDestFolder, Cnxn 
 
 ' do the move 
 rcDestFile.MoveRecord "", "https://MyServer/" & strFile, "", "", adMoveOverWrite 
 
 ' clean up 
 rsDestFolder.Close 
 Cnxn.Close 
 Set rsDestFolder = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rsDestFolder Is Nothing Then 
 If rsDestFolder.State = adStateOpen Then rsDestFolder.Close 
 End If 
 Set rsDestFolder = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
'EndDeleteRecordVB 
```

