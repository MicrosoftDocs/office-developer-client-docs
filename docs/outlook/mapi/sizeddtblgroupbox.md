---
title: "SizedDtblGroupBox"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedDtblGroupBox
api_type:
- COM
ms.assetid: 7ca01bf7-5185-41cc-907e-01f256345997
description: "Creates a named structure that includes a DTBLGROUPBOX structure for describing a group box control and a label of a specified length."
---

# SizedDtblGroupBox

**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named structure that includes a [DTBLGROUPBOX](dtblgroupbox.md) structure for describing a group box control and a label of a specified length. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLGROUPBOX** <br/> |
   
```cpp
SizedDtblGroupBox (n, u)
```

## Parameters

_n_
  
> Length of the group box's label. 
    
_u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblGroupBox** macro lets you define a group box control when the length of the label is known. The new structure is created with the following members: 
  
```cpp
DTBLGROUPBOX dtblgroupbox;
TCHAR lpszLabel[n];

```

To use a pointer to the resulting structure from the **SizedDtblGroupBox** macro as a **DTBLGROUPBOX** structure pointer, perform the following cast: 
  
```cpp
lpDtblGroupBox = (LPDTBLGROUPBOX) &SizedDtblGroupBox;

```

## See also

- [DTBLGROUPBOX](dtblgroupbox.md)
- [Macros Related to Structures](macros-related-to-structures.md)

