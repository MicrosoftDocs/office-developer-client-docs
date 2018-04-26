---
title: "BeginTrans, CommitTrans, and RollbackTrans Methods Example (VB)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 12fce322-dba7-9159-8a09-7f6daf1a80ed
description: "This example changes the book type of all psychology books in the Titles table of the database. After the BeginTrans method starts a transaction that isolates all the changes made to the Titles table, the CommitTrans method saves the changes. You can use the RollbackTrans method to undo changes that you saved using the Update method."
---

# BeginTrans, CommitTrans, and RollbackTrans Methods Example (VB)

This example changes the book type of all psychology books in the ** *Titles* ** table of the database. After the [BeginTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) method starts a transaction that isolates all the changes made to the ** *Titles* ** table, the [CommitTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) method saves the changes. You can use the [RollbackTrans](begintrans-committrans-and-rollbacktrans-methods-ado.md) method to undo changes that you saved using the [Update](update-method-ado.md) method. 
  
```
 
'BeginBeginTransVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'recordset and connection variables 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 Dim rstTitles As ADODB.Recordset 
 Dim strSQLTitles As String 
 'record variables 
 Dim strTitle As String 
 Dim strMessage As String 
 
 ' Open connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Set Cnxn = New ADODB.Connection 
 Cnxn.Open strCnxn 
 
 ' Open recordset dynamic to allow for changes 
 Set rstTitles = New ADODB.Recordset 
 strSQLTitles = "Titles" 
 rstTitles.Open strSQLTitles, Cnxn, adOpenDynamic, adLockPessimistic, adCmdTable 
 
 Cnxn.BeginTrans 
 
 ' Loop through recordset and prompt user 
 ' to change the type for a specified title 
 
 rstTitles.MoveFirst 
 
 Do Until rstTitles.EOF 
 If Trim(rstTitles!Type) = "psychology" Then 
 strTitle = rstTitles!Title 
 strMessage = "Title: " &amp; strTitle &amp; vbCr &amp; _ 
 "Change type to self help?" 
 
 ' If yes, change type for the specified title 
 If MsgBox(strMessage, vbYesNo) = vbYes Then 
 rstTitles!Type = "self_help" 
 rstTitles.Update 
 End If 
 End If 
 rstTitles.MoveNext 
 Loop 
 
 ' Prompt user to commit all changes made 
 If MsgBox("Save all changes?", vbYesNo) = vbYes Then 
 Cnxn.CommitTrans 
 Else 
 Cnxn.RollbackTrans 
 End If 
 
 ' Print recordset 
 rstTitles.Requery 
 rstTitles.MoveFirst 
 Do While Not rstTitles.EOF 
 Debug.Print rstTitles!Title &amp; " - " &amp; rstTitles!Type 
 rstTitles.MoveNext 
 Loop 
 
 ' Restore original data as this is a demo 
 rstTitles.MoveFirst 
 
 Do Until rstTitles.EOF 
 If Trim(rstTitles!Type) = "self_help" Then 
 rstTitles!Type = "psychology" 
 rstTitles.Update 
 End If 
 rstTitles.MoveNext 
 Loop 
 
 ' clean up 
 rstTitles.Close 
 Cnxn.Close 
 Set rstTitles = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstTitles Is Nothing Then 
 If rstTitles.State = adStateOpen Then rstTitles.Close 
 End If 
 Set rstTitles = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
 
'EndBeginTransVB 

```


