---
title: "Step 3 Server Obtains a Recordset (RDS Tutorial)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fadb6a9b-ed44-264f-22fd-26b121f98040
description: "The server program uses the connect string and command text to query the data source for the desired rows. ADO is typically used to retrieve this Recordset , although other Microsoft data access interfaces, such as OLE DB, could be used."
---

# Step 3: Server Obtains a Recordset (RDS Tutorial)

The server program uses the connect string and command text to query the data source for the desired rows. ADO is typically used to retrieve this **Recordset**, although other Microsoft data access interfaces, such as OLE DB, could be used. 
  
A custom server program might look like this:
  
```
 
Public Function ServerProgram(cn as String, qry as String) as Object 
Dim rs as New ADODB.Recordset 
 rs.CursorLocation = adUseClient 
 rs.Open qry, cn 
 rs.ActiveConnection = Nothing 
 Set ServerProgram = rs 
End Function 

```


