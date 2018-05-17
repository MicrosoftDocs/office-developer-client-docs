---
title: "MAPIGetDefaultMalloc"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPIGetDefaultMalloc
api_type:
- HeaderDef
ms.assetid: 148695dd-d886-4a06-9cfe-749059ae91ed
description: "Last modified: March 09, 2015"
---

# MAPIGetDefaultMalloc

  
  
**Applies to**: Outlook 
  
Retrieves the address of the default MAPI memory allocation function.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
LPMALLOC MAPIGetDefaultMalloc( );
```

## Parameters

None. 
  
## Return value

The **MAPIGetDefaultMalloc** function returns a pointer to the default MAPI memory allocation function. 
  

