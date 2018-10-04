﻿---
title: Status Property Example (Recordset) (VB)
TOCTitle: Status Property Example (Recordset) (VB)
ms:assetid: 97ddd465-88ed-81dd-3714-1841f1c87611
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249677(v=office.15)
ms:contentKeyID: 48546476
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Status Property Example (Recordset) (VB)


**Applies to**: Access 2013 | Office 2013

This example uses the [Status](status-property-ado-recordset.md) property to display which records have been modified in a batch operation before a batch update has occurred.

``` 
 
'BeginStatusRecordsetVB 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
 ' connection and recordset variables 
 Dim rstTitles As ADODB.Recordset 
 Dim Cnxn As ADODB.Connection 
 Dim strCnxn As String 
 Dim strSQLTitles As String 
 
 ' open connection 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 ' open recordset for batch update 
 Set rstTitles = New ADODB.Recordset 
 strSQLTitles = "Titles" 
 rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockBatchOptimistic, adCmdTable 
 
 ' change the type of psychology titles 
 Do Until rstTitles.EOF 
 If Trim(rstTitles!Type) = "psychology" Then rstTitles!Type = "self_help" 
 rstTitles.MoveNext 
 Loop 
 
 ' display Title ID and status 
 rstTitles.MoveFirst 
 Do Until rstTitles.EOF 
 If rstTitles.Status = adRecModified Then 
 Debug.Print rstTitles!title_id & " - Modified" 
 Else 
 Debug.Print rstTitles!title_id 
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
 If rstTitles.State = adStateOpen Then 
 ' Cancel the update because this is a demonstration 
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
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
'EndStatusRecordsetVB 
```

