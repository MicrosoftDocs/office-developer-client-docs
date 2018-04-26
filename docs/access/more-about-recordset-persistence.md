---
title: "More About Recordset Persistence"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f3248de7-6eef-1dd0-ff96-557b411789e7
description: "The ADO Recordset object supports storing a Recordset object's contents in a file using its Save method. The persistently stored file may exist on a local drive, network server, or as a URL on a Web site. Later, the file can be restored with either the Recordset object's Open method or the Connection object's Execute method."
---

# More About Recordset Persistence

The ADO Recordset object supports storing a **Recordset** object's contents in a file using its [Save](save-method-ado.md) method. The persistently stored file may exist on a local drive, network server, or as a URL on a Web site. Later, the file can be restored with either the **Recordset** object's [Open](open-method-ado-recordset.md) method or the [Connection](connection-object-ado.md) object's [Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx) method. 
  
In addition, the [GetString](getstring-method-ado.md) method converts a **Recordset** object to a form in which the columns and rows are delimited with characters you specify. 
  
To persist a **Recordset**, begin by converting it to a form that can be stored in a file. **Recordset** objects can be stored in the proprietary Advanced Data TableGram (ADTG) format or the open Extensible Markup Language (XML) format. ADTG examples are shown below. For more information about XML persistence, see [Persisting Records in XML format](persisting-records-in-xml-format.md).
  
Save any pending changes in the persisted file. Doing this allows you to issue a query that returns a **Recordset** object, edits the **Recordset**, saves it and the pending changes, later restores the **Recordset**, and then updates the data source with the saved pending changes. 
  
For information about persistently storing **Stream** objects, see [Streams and Persistence](streams-and-persistence.md) in Chapter 10. 
  
For an example of **Recordset** persistence, see the [XML Recordset Persistence Scenario](xml-recordset-persistence-scenario.md).
  
## Example

 **Save a Recordset:**
  
```
 
Dim rs as New ADODB.Recordset 
rs.Save "c:\yourFile.adtg", adPersistADTG 

```

 **Open a persisted file with Recordset.Open:**
  
```
 
Dim rs as New ADODB.Recordset 
rs.Open "c:\yourFile.adtg", "Provider='MSPersist'",,,adCmdFile
```

Optionally, if the **Recordset** does not have an active connection, you can accept all the defaults and simply code the following: 
  
```
 
Dim rs as New ADODB.Recordset 
rs.Open "c:\yourFile.adtg" 

```

 **Open a persisted file with Connection.Execute:**
  
```
 
Dim conn as New ADODB.Connection 
Dim rs as ADODB.Recordset 
conn.Open "Provider='MSPersist'" 
Set rs = conn.execute("c:\yourFile.adtg") 

```

 **Open a persisted file with RDS.DataControl:**
  
In this case, the **Server** property is not set. 
  
```
 
Dim dc as New RDS.DataControl 
dc.Connection = "Provider='MSPersist'" 
dc.SQL = "c:\yourFile.adtg" 
dc.Refresh
```


