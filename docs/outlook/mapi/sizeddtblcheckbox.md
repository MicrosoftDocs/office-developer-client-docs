---
title: "SizedDtblCheckBox"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblCheckBox
api_type:
- COM
ms.assetid: 9d04a124-54d4-43ac-967f-ea8e7a09b1d0
description: "Last modified: March 09, 2015"
---

# SizedDtblCheckBox
 
**Applies to**: Outlook 
  
Creates a named structure that includes a [DTBLCHECKBOX](dtblcheckbox.md) structure for describing a check box control and a label of a specified length. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLCHECKBOX** <br/> |
   
```cpp
SizedDtblCheckBox (n, u)
```

## Parameters

_n_
  
> Length of the label to be included in the new structure.
    
_u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblCheckBox** macro lets you define a check box when the number of label characters is known. The new structure is created with the following members: 
  
```cpp
DTBLCHECKBOX dtblcheckbox;
TCHAR lpszLabel[n];
```

To use a pointer to the resulting structure from the **SizedDtblCheckBox** macro as a **DTBLCHECKBOX** structure pointer, perform the following cast: 
  
```cpp
lpDtblCheckBox = (LPDTBLCHECKBOX) &SizedDtblCheckBox;
```

## See also

- [DTBLCHECKBOX](dtblcheckbox.md)
- [Macros Related to Structures](macros-related-to-structures.md)

