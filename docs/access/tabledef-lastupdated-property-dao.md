---
title: "TableDef.LastUpdated Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fafe54e2-2cf0-5874-92b9-6e20a65e77ef
description: "Returns the date and time of the most recent change made to an object. Read-only Variant ."
---

# TableDef.LastUpdated Property (DAO)

Returns the date and time of the most recent change made to an object. Read-only **Variant**. 
  
## Syntax

 *expression*  . **LastUpdated**
  
 *expression*  A variable that represents a **TableDef** object. 
  
## Remarks

 **DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings. 
  

