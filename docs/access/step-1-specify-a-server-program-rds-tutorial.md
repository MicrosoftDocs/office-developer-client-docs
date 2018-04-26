---
title: "Step 1 Specify a Server Program (RDS Tutorial)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: e6c2c624-d9bc-c899-60bc-e80a67ce8596
description: "In the most general case, use the RDS.DataSpace object CreateObject method to specify the default server program, RDSServer.DataFactory, or your own custom server program (business object). A server program is instantiated on the server, and a reference to the server program, or proxy , is returned."
---

# Step 1: Specify a Server Program (RDS Tutorial)

In the most general case, use the [RDS.DataSpace](dataspace-object-rds.md) object [CreateObject](createobject-method-rds.md) method to specify the default server program, [RDSServer.DataFactory](datafactory-object-rdsserver.md), or your own custom server program (business object). A server program is instantiated on the server, and a reference to the server program, or  *proxy*  , is returned. 
  
This tutorial uses the default server program:
  
```
 
Sub RDSTutorial1() 
 Dim DS as New RDS.DataSpace 
 Dim DF as Object 
 Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
... 

```


