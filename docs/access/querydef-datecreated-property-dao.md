---
title: "QueryDef.DateCreated Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f7585b34-8314-fb9f-daa6-cd1a8ad59d91
description: "Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only Variant ."
---

# QueryDef.DateCreated Property (DAO)

Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only **Variant**. 
  
## Syntax

 *expression*  . **DateCreated**
  
 *expression*  A variable that represents a **QueryDef** object. 
  
## Remarks

 **DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings. 
  

