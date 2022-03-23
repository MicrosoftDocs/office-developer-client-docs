---
title: "SizedENTRYID"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedENTRYID
api_type:
- COM
ms.assetid: 491170af-db35-4d7e-a912-44ffe8c7506b
description: "Creates a named ENTRYID structure that contains an ab member of a specified size. Use this macro to create an entry identifier with explicit bounds."
---

# SizedENTRYID

**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named [ENTRYID](entryid.md) structure that contains an **ab** member of a specified size. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**ENTRYID** <br/> |
   
```cpp
SizedENTRYID (_cb, _name)
```

## Parameters

__cb_
  
> Count of bytes in the **ab** member of the new structure. 
    
__name_
  
> Name for the new structure.
    
## Remarks

The **SizedENTRYID** macro lets you define an entry identifier after array length requirements are known. Use this macro to create an entry identifier with explicit bounds. 
  
To use the new structure that results from the **SizedENTRYID** macro as a pointer to an **ENTRYID** structure, perform the following cast: 
  
```cpp
lpENTRYID = (LPENTRYID) &SizedENTRYID;

```

## See also

- [ENTRYID](entryid.md)
- [Macros Related to Structures](macros-related-to-structures.md)

