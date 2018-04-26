---
title: "Hybrid Commands"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 55654274-0494-349f-820d-92108284449d
description: "Hybrid commands are partially parameterized commands. For example:"
---

# Hybrid Commands

Hybrid commands are partially parameterized commands. For example:
  
```
 
SHAPE {select * from plants} 
 APPEND( {select * from customers where country = ?} 
 RELATE PlantCountry TO PARAMETER 0, 
 PlantRegion TO CustomerRegion ) 

```

The caching behavior for a hybrid command is the same as that of regular parameterized commands.
  

