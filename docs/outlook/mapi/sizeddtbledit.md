---
title: "SizedDtblEdit"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedDtblEdit
api_type:
- COM
ms.assetid: a658d027-03a2-4cde-bf99-563e8521cb31
description: "Creates a named structure that includes a DTBLEDIT structure for describing an edit control and the number of characters that can be entered in the control."
---

# SizedDtblEdit

**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named structure that includes a [DTBLEDIT](dtbledit.md) structure for describing an edit control and the maximum number of characters that can be entered in the control. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLEDIT** <br/> |
   
```cpp
SizedDtblEdit (n, u)
```

## Parameters

_n_
  
> Maximum number of characters that can be entered in the edit control.
    
_u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblEdit** macro lets you define an edit control when the number of enabled characters is known. The new structure is created with the following members: 
  
```cpp
DTBLEDIT dtbledit;
TCHAR lpszCharsAllowed[n];

```

To use a pointer to the resulting structure from the **SizedDtblEdit** macro as a **DTBLEDIT** structure pointer, perform the following cast: 
  
```cpp
lpDtblEdit = (LPDTBLEDIT) &SizedDtblEdit;

```

## See also

- [DTBLEDIT](dtbledit.md)
- [Macros Related to Structures](macros-related-to-structures.md)

