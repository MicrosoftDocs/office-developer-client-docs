---
title: "SizedDtblPage"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblPage
api_type:
- COM
ms.assetid: 47b2a69d-e902-429f-8b31-166b51aeaf7f
description: "Last modified: March 09, 2015"
---

# SizedDtblPage

**Applies to**: Outlook 
  
Creates a named structure that includes a [DTBLPAGE](dtblpage.md) structure for describing a tabbed page control, a label of a specified length, and a Help file entry of a specified length. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLPAGE** <br/> |
   
```cpp
SizedDtblPage (n, n1, u)
```

## Parameters

_n_
  
> Length of the label for the page tab.
    
_n1_
  
> Length of the entry appearing in the Mapisvc.inf file identifying the Help file that will be used with the tabbed page control.
    
_u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblPage** macro lets you define a tabbed page control when the number of characters in the associated label and Help file entry is known. The new structure is created with the following members: 
  
```cpp
DTBLPAGE dtblpage;
TCHAR lpszLabel[n];
TCHAR lpszComponent[n1];
```

To use a pointer to the resulting structure from the **SizedDtblPage** macro as a **DTBLPAGE** structure pointer, perform the following cast: 
  
```cpp
lpDtblPage = (LPDTBLPAGE) &SizedDtblPage;
```

## See also

- [DTBLPAGE](dtblpage.md)
- [Macros Related to Structures](macros-related-to-structures.md)

