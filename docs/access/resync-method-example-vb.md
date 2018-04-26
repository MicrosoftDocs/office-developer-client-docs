---
title: "Resync Method Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 831341e9-1aef-cd51-bc49-d3d70fd61471
description: "This example demonstrates using the Resync method to refresh data in a static recordset."
---

# Resync Method Example (VB)

This example demonstrates using the [Resync](resync-method-ado.md) method to refresh data in a static recordset. 
  
```
 
'BeginResyncVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection strings 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'connection and recordset variables 
 Dim Cnxn As ADODB.Connection 
 Dim rstTitles As ADODB.Recordset 
 Dim strCnxn As String 
 Dim strSQLTitles As String 
 
 ' Open connection 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 ' Open recordset using object refs to set properties 
 ' that allow for updates to the database 
 Set rstTitles = New ADODB.Recordset 
 Set rstTitles.ActiveConnection = Cnxn 
 rstTitles.CursorType = adOpenKeyset 
 rstTitles.LockType = adLockOptimistic 
 
 strSQLTitles = "titles" 
 rstTitles.Open strSQLTitles 
 
 'rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockPessimistic, adCmdTable 
 'the above line of code passes the same refs as the object refs listed above 
 
 ' Change the type of the first title in the recordset 
 rstTitles!Type = "database" 
 
 ' Display the results of the change 
 MsgBox "Before resync: " &amp; vbCr &amp; vbCr &amp; _ 
 "Title - " &amp; rstTitles!Title &amp; vbCr &amp; _ 
 "Type - " &amp; rstTitles!Type 
 
 ' Resync with database and redisplay results 
 rstTitles.Resync 
 MsgBox "After resync: " &amp; vbCr &amp; vbCr &amp; _ 
 "Title - " &amp; rstTitles!Title &amp; vbCr &amp; _ 
 "Type - " &amp; rstTitles!Type 
 
 ' clean up 
 rstTitles.CancelBatch 
 rstTitles.Close 
 Cnxn.Close 
 Set rstTitles = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstTitles Is Nothing Then 
 If rstTitles.State = adStateOpen Then 
 rstTitles.CancelBatch 
 rstTitles.Close 
 End If 
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
'EndResyncVB 

```


