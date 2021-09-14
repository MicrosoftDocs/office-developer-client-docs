---
title: "MAPIGetDefaultMalloc"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPIGetDefaultMalloc
api_type:
- HeaderDef
ms.assetid: 148695dd-d886-4a06-9cfe-749059ae91ed
description: "Last modified: March 09, 2015"
---

# MAPIGetDefaultMalloc

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the address of the default MAPI memory allocation function.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
LPMALLOC MAPIGetDefaultMalloc( );
```

## Parameters

None. 
  
## Return value

The **MAPIGetDefaultMalloc** function returns a pointer to the default MAPI memory allocation function. 
  

