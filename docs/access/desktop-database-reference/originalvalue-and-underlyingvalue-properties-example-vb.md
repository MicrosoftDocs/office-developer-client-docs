---
title: OriginalValue and UnderlyingValue Properties Example (VB)
TOCTitle: OriginalValue and UnderlyingValue Properties Example (VB)
ms:assetid: de88d99d-7f2e-8418-b40f-0375b1d90a8e
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250127(v=office.15)
ms:contentKeyID: 48548189
ms.date: 09/18/2015
mtps_version: v=office.15
---

# OriginalValue and UnderlyingValue Properties Example (VB)

**Applies to**: Access 2013, Office 2013

This example demonstrates the [OriginalValue](originalvalue-property-ado.md) and [UnderlyingValue](underlyingvalue-property-ado.md) properties by displaying a message if a record's underlying data has changed during a [Recordset](recordset-object-ado.md) batch update.

```vb 
 
'BeginOriginalValueVB 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
 Dim Cnxn As ADODB.Connection 
 Dim rstTitles As ADODB.Recordset 
 Dim fldType As ADODB.Field 
 Dim strCnxn As String 
 Dim strSQLTitles As String 
 
 ' Open connection. 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 ' Open recordset for batch update 
 ' using object refs to set properties 
 Set rstTitles = New ADODB.Recordset 
 Set rstTitles.ActiveConnection = Cnxn 
 rstTitles.CursorType = adOpenKeyset 
 rstTitles.LockType = adLockBatchOptimistic 
 strSQLTitles = "titles" 
 rstTitles.Open strSQLTitles 
 
 ' Set field object variable for Type field 
 Set fldType = rstTitles!Type 
 
 ' Change the type of psychology titles 
 Do Until rstTitles.EOF 
 If Trim(fldType) = "psychology" Then 
 fldType = "self_help" 
 End If 
 rstTitles.MoveNext 
 Loop 
 
 ' Similate a change by another user by updating 
 ' data using a command string 
 Cnxn.Execute "UPDATE Titles SET type = 'sociology' " & _ 
 "WHERE type = 'psychology'" 
 
 'Check for changes 
 rstTitles.MoveFirst 
 Do Until rstTitles.EOF 
 If fldType.OriginalValue <> fldType.UnderlyingValue Then 
 MsgBox "Data has changed!" & vbCr & vbCr & _ 
 " Title ID: " & rstTitles!title_id & vbCr & _ 
 " Current value: " & fldType & vbCr & _ 
 " Original value: " & _ 
 fldType.OriginalValue & vbCr & _ 
 " Underlying value: " & _ 
 fldType.UnderlyingValue & vbCr 
 End If 
 rstTitles.MoveNext 
 Loop 
 
 ' Cancel the update because this is a demonstration 
 rstTitles.CancelBatch 
 
 ' Restore original values 
 Cnxn.Execute "UPDATE Titles SET type = 'psychology' " & _ 
 "WHERE type = 'sociology'" 
 
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
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
'EndOriginalValueVB 
```

