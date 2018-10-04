---
title: 'Step 1: Specify a Server Program (RDS Tutorial)'
TOCTitle: 'Step 1: Specify a Server Program (RDS Tutorial)'
ms:assetid: e6c2c624-d9bc-c899-60bc-e80a67ce8596
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250172(v=office.15)
ms:contentKeyID: 48548389
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Step 1: Specify a Server Program (RDS Tutorial)


_**Applies to:** Access 2013 | Office 2013_

In the most general case, use the [RDS.DataSpace](dataspace-object-rds.md) object [CreateObject](createobject-method-rds.md) method to specify the default server program, [RDSServer.DataFactory](datafactory-object-rdsserver.md), or your own custom server program (business object). A server program is instantiated on the server, and a reference to the server program, or *proxy*, is returned.

This tutorial uses the default server program:

``` 
 
Sub RDSTutorial1() 
 Dim DS as New RDS.DataSpace 
 Dim DF as Object 
 Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer") 
... 
```

