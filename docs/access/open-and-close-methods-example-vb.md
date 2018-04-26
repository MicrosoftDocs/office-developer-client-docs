---
title: "Open and Close Methods Example (VB)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5c000d5f-2560-2530-fe36-163f6600f3cc
description: "This example uses the Open and Close methods on both Recordset and Connection objects that have been opened."
---

# Open and Close Methods Example (VB)

This example uses the **Open** and [Close](close-method-ado.md) methods on both [Recordset](recordset-object-ado.md) and [Connection](connection-object-ado.md) objects that have been opened. 
  
```
 
'BeginOpenVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub OpenX() 
 On Error GoTo ErrorHandler 
 
 Dim Cnxn As ADODB.Connection 
 Dim rstEmployees As ADODB.Recordset 
 Dim strCnxn As String 
 Dim strSQLEmployees As String 
 Dim varDate As Variant 
 
 ' Open connection 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 Set Cnxn = New ADODB.Connection 
 Cnxn.Open strCnxn 
 
 ' Open employee table 
 Set rstEmployees = New ADODB.Recordset 
 strSQLEmployees = "employee" 
 rstEmployees.Open strSQLEmployees, Cnxn, adOpenKeyset, adLockOptimistic, adCmdTable 
 
 ' Assign the first employee record's hire date 
 ' to a variable, then change the hire date 
 varDate = rstEmployees!hire_date 
 Debug.Print "Original data" 
 Debug.Print " Name - Hire Date" 
 Debug.Print " " &amp; rstEmployees!fname &amp; " " &amp; _ 
 rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date 
 rstEmployees!hire_date = #1/1/1900# 
 rstEmployees.Update 
 Debug.Print "Changed data" 
 Debug.Print " Name - Hire Date" 
 Debug.Print " " &amp; rstEmployees!fname &amp; " " &amp; _ 
 rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date 
 
 ' Requery Recordset and reset the hire date 
 rstEmployees.Requery 
 rstEmployees!hire_date = varDate 
 rstEmployees.Update 
 Debug.Print "Data after reset" 
 Debug.Print " Name - Hire Date" 
 Debug.Print " " &amp; rstEmployees!fname &amp; " " &amp; _ 
 rstEmployees!lname &amp; " - " &amp; rstEmployees!hire_date 
 
 ' clean up 
 rstEmployees.Close 
 Cnxn.Close 
 Set rstEmployees = Nothing 
 Set Cnxn = Nothing 
 Exit Sub 
 
ErrorHandler: 
 ' clean up 
 If Not rstEmployees Is Nothing Then 
 If rstEmployees.State = adStateOpen Then rstEmployees.Close 
 End If 
 Set rstEmployees = Nothing 
 
 If Not Cnxn Is Nothing Then 
 If Cnxn.State = adStateOpen Then Cnxn.Close 
 End If 
 Set Cnxn = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source &amp; "-->" &amp; Err.Description, , "Error" 
 End If 
End Sub 
'EndOpenVB 

```


