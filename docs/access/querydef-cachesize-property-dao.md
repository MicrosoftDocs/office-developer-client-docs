---
title: "QueryDef.CacheSize Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a84d990e-8180-daa3-7640-47d2be8fd28b
description: "Sets or returns the number of records retrieved from an ODBC data source that will be cached locally. Read/write Long ."
---

# QueryDef.CacheSize Property (DAO)

Sets or returns the number of records retrieved from an ODBC data source that will be cached locally. Read/write **Long**. 
  
## Syntax

 *expression*  . **CacheSize**
  
 *expression*  A variable that represents a **QueryDef** object. 
  
## Remarks

The value of the **CacheSize** property must be between 5 and 1200, but not greater than available memory will allow. A typical value is 100. A setting of 0 turns off caching. 
  
The Microsoft Access database engine requests records within the cache range from the cache, and it requests records outside the cache range from the server.
  
Records retrieved from the cache don't reflect concurrent changes that other users made to the source data.
  

