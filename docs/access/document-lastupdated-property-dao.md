---
title: "Document.LastUpdated Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 9307ceee-095f-0364-fd5b-905bc523b9c0
description: "Returns the date and time of the most recent change made to an object. Read-only Variant ."
---

# Document.LastUpdated Property (DAO)

Returns the date and time of the most recent change made to an object. Read-only **Variant**. 
  
## Syntax

 *expression*  . **LastUpdated**
  
 *expression*  A variable that represents a **Document** object. 
  
## Remarks

 **DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings. 
  

