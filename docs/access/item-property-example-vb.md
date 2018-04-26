---
title: "Item Property Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e8d17560-8a0d-7045-d8dc-728a85037c0d
description: "This example demonstrates how the Item property accesses members of a collection. The example opens the Authors table of the Pubs database with a parameterized command."
---

# Item Property Example (VB)

This example demonstrates how the [Item](item-property-ado.md) property accesses members of a collection. The example opens the ** *Authors* ** table of the ** *Pubs* ** database with a parameterized command. 
  
The parameter in the command issued against the database is accessed from the [Command](command-object-ado.md) object's [Parameters](parameters-collection-ado.md) collection by index and name. The fields of the returned [Recordset](recordset-object-ado.md) are then accessed from that object's [Fields](fields-collection-ado.md) collection by index and name. 
  
```
 
'BeginItemVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 Dim Cnxn As ADODB.Connection 
 Dim rstAuthors As ADODB.Recordset 
 Dim cmd As ADODB.Command 
 Dim prm As ADODB.Parameter 
 Dim fld As ADODB.Field 
 Dim strCnxn As String 
 
 Dim ix As Integer 
 Dim limit As Long 
 Dim Column(0 To 8) As Variant 
 
 Set Cnxn = New ADODB.Connection 
 Set rstAuthors = New ADODB.Recordset 
 Set cmd = New ADODB.Command 
 
 'Set the array with the Authors table field (column) names 
 Column(0) = "au_id" 
 Column(1) = "au_lname" 
 Column(2) = "au_fname" 
 Column(3) = "phone" 
 Column(4) = "address" 
 Column(5) = "city" 
 Column(6) = "state" 
 Column(7) = "zip" 
 Column(8) = "contract" 
 
 cmd.CommandText = "SELECT * FROM Authors WHERE state = ?" 
 Set prm = cmd.CreateParameter("ItemXparm", adChar, adParamInput, 2, "CA") 
 cmd.Parameters.Append prm 
 ' set connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 cmd.ActiveConnection = Cnxn 
 ' open recordset 
 rstAuthors.Open cmd, , adOpenStatic, adLockReadOnly 
 'Connection and CommandType are omitted because 
 'a Command object is provided 
 
 Debug.Print "The Parameters collection accessed by index..." 
 Set prm = cmd.Parameters.Item(0) 
 Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'" 
 Debug.Print 
 
 Debug.Print "The Parameters collection accessed by name..." 
 Set prm = cmd.Parameters.Item("ItemXparm") 
 Debug.Print "Parameter name = '"; prm.Name; "', value = '"; prm.Value; "'" 
 Debug.Print 
 
 Debug.Print "The Fields collection accessed by index..." 
 
 rstAuthors.MoveFirst 
 limit = rstAuthors.Fields.Count - 1 
 For ix = 0 To limit 
 Set fld = rstAuthors.Fields.Item(ix) 
 Debug.Print "Field "; ix; ": Name = '"; fld.Name; _ 
 "', Value = '"; fld.Value; "'" 
 Next ix 
 
 Debug.Print 
 
 Debug.Print "The Fields collection accessed by name..." 
 
 rstAuthors.MoveFirst 
 For ix = 0 To 8 
 Set fld = rstAuthors.Fields.Item(Column(ix)) 
 Debug.Print "Field name = '"; fld.Name; "', Value = '"; fld.Value; "'" 
 Next ix 
 
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
 
 Set cmd = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
 
End Sub 
'EndItemVB 

```


