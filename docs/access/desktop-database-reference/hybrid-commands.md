---
title: Hybrid commands (Access desktop database reference)
TOCTitle: Hybrid commands
ms:assetid: 55654274-0494-349f-820d-92108284449d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249286(v=office.15)
ms:contentKeyID: 48544929
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Hybrid commands


**Applies to**: Access 2013, Office 2013

Hybrid commands are partially parameterized commands. For example:

```vb 
 
SHAPE {select * from plants} 
 APPEND( {select * from customers where country = ?} 
 RELATE PlantCountry TO PARAMETER 0, 
 PlantRegion TO CustomerRegion ) 
```

The caching behavior for a hybrid command is the same as that of regular parameterized commands.

