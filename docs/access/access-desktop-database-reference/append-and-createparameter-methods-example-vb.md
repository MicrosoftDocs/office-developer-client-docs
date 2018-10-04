﻿---
title: Append and CreateParameter Methods Example (VB)
TOCTitle: Append and CreateParameter Methods Example (VB)
ms:assetid: 0b7a5329-4be3-2854-530d-fb01213f34f9
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248846(v=office.15)
ms:contentKeyID: 48543177
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Append and CreateParameter Methods Example (VB)


**Applies to**: Access 2013 | Office 2013

This example uses the [Append](append-method-ado.md) and [CreateParameter](createparameter-method-ado.md) methods to execute a stored procedure with an input parameter.

``` 
 
'BeginAppendVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 'recordset, command and connection variables 
 Dim Cnxn As ADODB.Connection 
 Dim cmdByRoyalty As ADODB.Command 
 Dim prmByRoyalty As ADODB.Parameter 
 Dim rstByRoyalty As ADODB.Recordset 
 Dim rstAuthors As ADODB.Recordset 
 Dim strCnxn As String 
 Dim strSQLAuthors As String 
 Dim strSQLByRoyalty As String 
 'record variables 
 Dim intRoyalty As Integer 
 Dim strAuthorID As String 
 
 ' Open connection 
 Set Cnxn = New ADODB.Connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Cnxn.Open strCnxn 
 
 ' Open command object with one parameter 
 Set cmdByRoyalty = New ADODB.Command 
 cmdByRoyalty.CommandText = "byroyalty" 
 cmdByRoyalty.CommandType = adCmdStoredProc 
 
 ' Get parameter value and append parameter 
 intRoyalty = Trim(InputBox("Enter royalty:")) 
 Set prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput) 
 cmdByRoyalty.Parameters.Append prmByRoyalty 
 prmByRoyalty.Value = intRoyalty 
 
 ' Create recordset by executing the command 
 Set cmdByRoyalty.ActiveConnection = Cnxn 
 Set rstByRoyalty = cmdByRoyalty.Execute 
 
 ' Open the Authors Table to get author names for display 
 ' and set cursor client-side 
 Set rstAuthors = New ADODB.Recordset 
 strSQLAuthors = "Authors" 
 rstAuthors.Open strSQLAuthors, Cnxn, adUseClient, adLockOptimistic, adCmdTable 
 
 ' Print recordset adding author names from Authors table 
 Debug.Print "Authors with " & intRoyalty & " percent royalty" 
 
 Do Until rstByRoyalty.EOF 
 strAuthorID = rstByRoyalty!au_id 
 Debug.Print " " & rstByRoyalty!au_id & ", "; 
 rstAuthors.Filter = "au_id = '" & strAuthorID & "'" 
 Debug.Print rstAuthors!au_fname & " " & rstAuthors!au_lname 
 rstByRoyalty.MoveNext 
 Loop 
 
 ' clean up 
 rstByRoyalty.Close 
 rstAuthors.Close 
 Cnxn.Close 
 Set rstByRoyalty = Nothing 
 Set rstAuthors = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstByRoyalty Is Nothing Then 
 If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close 
 End If 
 Set rstByRoyalty = Nothing 
 
 If Not rstAuthors Is Nothing Then 
 If rstAuthors.State = adStateOpen Then rstAuthors.Close 
 End If 
 Set rstAuthors = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
End Sub 
'EndAppendVB 
```

