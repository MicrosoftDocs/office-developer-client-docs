---
title: "RDS Tutorial (Visual J++)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: b5679bfe-e830-05df-8a1c-0744c96abe90
description: "ADO/WFC does not completely follow the RDS object model in that it does not implement the RDS.DataControl object. ADO/WFC only implements the client-side class, RDS.DataSpace."
---

# RDS Tutorial (Visual J++)

ADO/WFC does not completely follow the RDS object model in that it does not implement the [RDS.DataControl](datacontrol-object-rds.md) object. ADO/WFC only implements the client-side class, [RDS.DataSpace](dataspace-object-rds.md).
  
The **DataSpace** class implements one method, [CreateObject](createobject-method-rds.md), which returns an [ObjectProxy](http://msdn.microsoft.com/library/8e3224b7-0b1d-1e08-eaa7-ceb0b6f5411c%28Office.15%29.aspx) object. The **DataSpace** class also implements the [InternetTimeout](internettimeout-property-rds.md) property. 
  
The **ObjectProxy** class implements one method, call, which can invoke any server-side business object. 
  
 **This is the beginning of the tutorial.**
  
```
 
import com.ms.wfc.data.*; 
public class RDSTutorial 
{ 
 public void tutorial() 
 { 
// Step 1: Specify a server program. 
 ObjectProxy obj = 
 DataSpace.createObject( 
 "RDSServer.DataFactory", 
 "http://YourServer"); 
 
// Step 2: Server returns a Recordset. 
 Recordset rs = (Recordset) obj.call( 
 "Query", 
 new Object[] {"DSN=Pubs;", "SELECT * FROM Authors"}); 
 
// Step 3: Changes are sent to the server. 
 ... // Edit Recordset. 
 obj.call( 
 "SubmitChanges", 
 new Object[] {"DSN=Pubs;", rs}); 
 return; 
 } 
} 

```

 **This is the end of the tutorial.**
  

