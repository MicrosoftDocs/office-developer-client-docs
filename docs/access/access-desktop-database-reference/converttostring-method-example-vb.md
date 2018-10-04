﻿---
title: ConvertToString Method Example (VB)
TOCTitle: ConvertToString Method Example (VB)
ms:assetid: a75f9d56-7043-34b0-ab78-e146c4a69e15
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249772(v=office.15)
ms:contentKeyID: 48546875
ms.date: 09/18/2015
mtps_version: v=office.15
---

# ConvertToString Method Example (VB)


**Applies to**: Access 2013 | Office 2013

``` 
 
'BeginConvertToStringVB 
 
 'To integrate this code 
 'replace the data source and initial catalog values 
 'in the connection string 
 
Public Sub Main() 
 On Error GoTo ErrorHandler 
 
 ' to integrate this code replace the server name 
 ' in the CreateObject call 
 
 ' RDS variables 
 Dim rdsDS As RDS.DataSpace 
 Dim rdsDC As RDS.DataControl 
 Dim rdsDF As Object 
 ' recordset and connection variables 
 Dim rsAuthors As ADODB.Recordset 
 Dim strSQLAuthors As String 
 Dim strCnxn As String 
 Dim varString As Variant 
 
 ' Create a DataSpace object 
 Set rdsDS = New RDS.DataSpace 
 ' Create a DataFactory object 
 Set rdsDF = rdsDS.CreateObject("RDSServer.DataFactory", "https://MyServer") 'MyServer 
 
 ' Get all of the Author records 
 
 strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _ 
 "Initial Catalog='Pubs';Integrated Security='SSPI';" 
 strSQLAuthors = "SELECT * FROM Authors" 
 Set rsAuthors = rdsDF.Query(strCnxn, strSQLAuthors) 
 ' Show results 
 Debug.Print "Old RDS recordset count:" & rsAuthors.RecordCount 
 
 ' Convert the recordset into a MIME formatted string 
 varString = rdsDF.ConvertToString(rsAuthors) 
 Debug.Print "Recordset as MIME format string:" 
 Debug.Print varString 
 
 ' Convert string value back into an ADO Recordset 
 Set rdsDC = New RDS.DataControl 
 rdsDC.SQL = varString 
 rdsDC.ExecuteOptions = adcExecSync 
 rdsDC.FetchOptions = adcFetchUpFront 
 rdsDC.Refresh 
 ' Show results 
 Debug.Print "New ADO recordset count:" & rdsDC.Recordset.RecordCount 
 
 ' clean up 
 rsAuthors.Close 
 Set rsAuthors = Nothing 
 Set rdsDC = Nothing 
 Set rdsDS = Nothing 
 Set rdsDC = Nothing 
 
ErrorHandler: 
 
 If Not rsAuthors Is Nothing Then 
 If rsAuthors.State = adStateOpen Then rsAuthors.Close 
 End If 
 Set rsAuthors = Nothing 
 Set rdsDC = Nothing 
 Set rdsDS = Nothing 
 Set rdsDC = Nothing 
 
 If Err <> 0 Then 
 MsgBox Err.Source & "-->" & Err.Description, , "Error" 
 End If 
 
End Sub 
'EndConvertToStringVB 
```

