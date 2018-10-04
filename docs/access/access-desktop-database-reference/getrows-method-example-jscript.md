﻿---
title: GetRows Method Example (JScript)
TOCTitle: GetRows Method Example (JScript)
ms:assetid: 72d7e2d9-1e19-e993-0b0e-5310405c9b75
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249466(v=office.15)
ms:contentKeyID: 48545620
ms.date: 09/18/2015
mtps_version: v=office.15
---

# GetRows Method Example (JScript)


**Applies to**: Access 2013 | Office 2013

This example uses the [GetRows](getrows-method-ado.md) method to retrieve all rows of the *Custiomers* table from a [Recordset](recordset-object-ado.md) and to fill an array with the resulting data. The **GetRows** method will return fewer than the desired number of rows in two cases: either if [EOF](bof-eof-properties-ado.md) has been reached, or if **GetRows** tried to retrieve a record that was deleted by another user. The function returns **False** only if the second case occurs. Cut and paste the following code to Notepad or another text editor, and save it as **GetRowsJS.asp**.

``` 
 
<!-- BeginGetRowsJS --> 
<%@ LANGUAGE="JScript" %> 
<%// use this meta tag instead of adojavas.inc%> 
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --> 
 
<html> 
 
<head> 
<title>ADO Recordset.GetRows Example (JScript)</title> 
<style> 
<!-- 
BODY { 
 font-family: 'Verdana','Arial','Helvetica',sans-serif; 
 BACKGROUND-COLOR:white; 
 COLOR:black; 
 } 
.thead { 
 background-color: #008080; 
 font-family: 'Verdana','Arial','Helvetica',sans-serif; 
 font-size: x-small; 
 color: white; 
 } 
.thead2 { 
 background-color: #800000; 
 font-family: 'Verdana','Arial','Helvetica',sans-serif; 
 font-size: x-small; 
 color: white; 
 } 
.tbody { 
 text-align: center; 
 background-color: #f7efde; 
 font-family: 'Verdana','Arial','Helvetica',sans-serif; 
 font-size: x-small; 
 } 
--> 
</style> 
</head> 
 
<body bgcolor="white"> 
 
<h1>ADO Recordset.GetRows Example (JScript)</h1> 
 <!-- Page text goes here --> 
<% 
 var Connect = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" + 
 "Initial Catalog='Northwind';Integrated Security='SSPI';"; 
 var mySQL = "select * from customers;"; 
 var showblank = " "; 
 var shownull = "-null-"; 
 
 var connTemp = Server.CreateObject("ADODB.Connection"); 
 
 try 
 { 
 connTemp.Open(Connect); 
 var rsTemp = Server.CreateObject("ADODB.Recordset"); 
 rsTemp.ActiveConnection = connTemp; 
 rsTemp.CursorLocation = adUseClient; 
 rsTemp.CursorType = adOpenKeyset; 
 rsTemp.LockType = adLockOptimistic; 
 rsTemp.Open(mySQL); 
 
 rsTemp.MoveFirst(); 
 
 if (rsTemp.RecordCount == 0) 
 { 
 Response.Write("No records matched "); 
 Response.Write (mySQL & "So cannot make table..."); 
 connTemp.Close(); 
 Response.End(); 
 } else 
 { 
 Response.Write('<table width="100%" border="2">'); 
 Response.Write('<tr class="thead2">'); 
 
 // Headings On The Table for each Field Name 
 for (var i=0; i<rsTemp.Fields.Count; i++) 
 { 
 fieldObject = rsTemp.fields(i); 
 Response.Write('<td width="' + Math.floor(100 / rsTemp.Fields.Count) + '%">' + fieldObject.name + "</td>"); 
 } 
 
 Response.Write("</tr>"); 
 
 // JScript doesn't support multi-dimensional arrays 
 // so we'll convert the returned array to a single 
 // dimensional JScript array and then display the data. 
 tempArray = rsTemp.GetRows(); 
 recArray = tempArray.toArray(); 
 
 var col = 1; 
 var maxCols = rsTemp.Fields.Count; 
 
 for (var thisField=0; thisField<recArray.length; thisField++) 
 { 
 if (col == 1) 
 Response.Write('<tr class="tbody">'); 
 if (recArray[thisField] == null) 
 recArray[thisField] = shownull; 
 if (recArray[thisField] == "") 
 recArray[thisField] = showblank; 
 Response.Write("<td>" + recArray[thisField] + "</td>"); 
 col++ 
 if (col > maxCols) 
 { 
 Response.Write("</tr>"); 
 col = 1; 
 } 
 } 
 Response.Write("</table>"); 
 } 
 } 
 catch (e) 
 { 
 Response.Write(e.message); 
 } 
 finally 
 { 
 // clean up 
 if (rsTemp.State == adStateOpen) 
 rsTemp.Close; 
 if (connTemp.State == adStateOpen) 
 connTemp.Close; 
 rsTemp = null; 
 connTemp = null; 
 } 
%> 
 
</body> 
 
</html> 
<!-- EndGetRowsJS --> 
 
```

