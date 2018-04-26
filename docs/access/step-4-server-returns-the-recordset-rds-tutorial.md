---
title: "Step 4 Server Returns the Recordset (RDS Tutorial)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 4503151d-de8b-98d1-1aa8-11f1b6e6b55c
description: "RDS converts the retrieved Recordset object to a form that can be sent back to the client (that is, it marshals the Recordset ). The exact form of the conversion and how it is sent depends on whether the server is on the Internet or an intranet, a local area network, or is a dynamic-link library. However, this detail is not critical; all that matters is that RDS sends the Recordset back to the client."
---

# Step 4: Server Returns the Recordset (RDS Tutorial)

RDS converts the retrieved **Recordset** object to a form that can be sent back to the client (that is, it  *marshals*  the **Recordset** ). The exact form of the conversion and how it is sent depends on whether the server is on the Internet or an intranet, a local area network, or is a dynamic-link library. However, this detail is not critical; all that matters is that RDS sends the **Recordset** back to the client. 
  
On the client side, a **Recordset** object is returned and assigned to a local variable. 
  
```
 
Sub RDSTutorial4() 
 Dim DS as New RDS.DataSpace 
 Dim RS as ADODB.Recordset 
 Dim DF as Object 
 Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
 Set RS = DF.Query("DSN=Pubs", "SELECT * FROM Authors") 
... 

```


