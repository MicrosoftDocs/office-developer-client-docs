---
title: "SizedDtblLabel"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedDtblLabel
api_type:
- COM
ms.assetid: c7cb8cf9-7abd-4ee3-b88c-d61695f4ed31
description: "Creates a named structure that includes a DTBLLABEL structure for describing a label control and the associated label of a specified length."
---

# SizedDtblLabel

**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named structure that includes a [DTBLLABEL](dtbllabel.md) structure for describing a label control and the associated label of a specified length. 
  
|Property |Value |
|:-----|:-----|
|Specified in header file:  <br/> |Mapidefs.h  <br/> |
|Related structure  <br/> |**DTBLLABEL** <br/> |
   
```cpp
SizedDtblLabel (n, u)
```

## Parameters

_n_
  
> Length of the label. This includes the ending NULL character. 
    
_u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblLabel** macro lets you define a display table label when the number of characters in the label is known. The new structure is created with the following members: 
  
```cpp
DTBLLABEL dtbllabel;
TCHAR lpszLabelName[n];
```

To use a pointer to the resulting structure from the **SizedDtblLabel** macro as a **DTBLLABEL** structure pointer, perform the following cast: 
  
```cpp
lpDtblLabel = (LPDTBLLABEL) &SizedDtblLabel;
```

## See also

- [DTBLLABEL](dtbllabel.md)
- [Macros Related to Structures](macros-related-to-structures.md)

