---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 61f82932-2ce9-341f-b120-168f786a9040
description: "This example uses the MoveFirst, MoveLast, MoveNext, and MovePrevious methods to move the record pointer of a Recordset based on the supplied command. The MoveAny procedure is required for this procedure to run."
---

# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VB)

This example uses the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveLast](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), [MoveNext](movefirst-movelast-movenext-and-moveprevious-methods-ado.md), and [MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) methods to move the record pointer of a [Recordset](recordset-object-ado.md) based on the supplied command. The MoveAny procedure is required for this procedure to run. 
  
```
 
'BeginMoveFirstVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 ' connection and recordset variables 
 Dim rstAuthors As ADODB.Recordset 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 Dim strSQLAuthors 
 ' record variables 
 Dim strMessage As String 
 Dim intCommand As Integer 
 
 ' Open connection 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 ' Open recordset from Authors table 
 Set rstAuthors = New ADODB.Recordset 
 rstAuthors.CursorLocation = adUseClient 
 ' Use client cursor to enable AbsolutePosition property 
 strSQLAuthors = "Authors" 
 rstAuthors.Open strSQLAuthors, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable 
 
 ' Show current record information and get user's method choice 
 Do 
 strMessage = "Name: " &amp; rstAuthors!au_fname &amp; " " &amp; _ 
 rstAuthors!au_lname &amp; vbCr &amp; "Record " &amp; _ 
 rstAuthors.AbsolutePosition &amp; " of " &amp; _ 
 rstAuthors.RecordCount &amp; vbCr &amp; vbCr &amp; _ 
 "[1 - MoveFirst, 2 - MoveLast, " &amp; vbCr &amp; _ 
 "3 - MoveNext, 4 - MovePrevious]" 
 intCommand = Val(Left(InputBox(strMessage), 1)) 
 
 ' for exiting the loop 
 If intCommand < 1 Or intCommand > 4 Then 
 MsgBox "You either entered a non-number or canceled the input box. Exit the application." 
 Exit Do 
 End If 
 
 ' Use specified method while trapping for BOF and EOF 
 Select Case intCommand 
 Case 1 
 rstAuthors.MoveFirst 
 Case 2 
 rstAuthors.MoveLast 
 Case 3 
 rstAuthors.MoveNext 
 If rstAuthors.EOF Then 
 MsgBox "Already at end of recordset!" 
 rstAuthors.MoveLast 
 End If 
 Case 4 
 rstAuthors.MovePrevious 
 If rstAuthors.BOF Then 
 MsgBox "Already at beginning of recordset!" 
 rstAuthors.MoveFirst 
 End If 
 End Select 
 Loop 
 
 ' clean up 
 rstAuthors.Close 
 Cnxn.Close 
 Set rstAuthors = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstAuthors Is Nothing Then 
 If rstAuthors.State = adStateOpen Then rstAuthors.Close 
 End If 
 Set rstAuthors = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
 
'EndMoveFirstVB 

```


