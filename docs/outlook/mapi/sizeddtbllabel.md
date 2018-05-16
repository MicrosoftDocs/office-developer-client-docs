---
title: "SizedDtblLabel"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblLabel
api_type:
- COM
ms.assetid: c7cb8cf9-7abd-4ee3-b88c-d61695f4ed31
description: "Last modified: March 09, 2015"
---

# SizedDtblLabel

  
  
**Applies to**: Outlook 
  
Creates a named structure that includes a [DTBLLABEL](dtbllabel.md) structure for describing a label control and the associated label of a specified length. 
  
|||
|:-----|:-----|
|Specified in header file:  <br/> |Mapidefs.h  <br/> |
|Related structure  <br/> |**DTBLLABEL** <br/> |
   
```
SizedDtblLabel (n, u)
```

## Parameters

 _n_
  
> Length of the label. This includes the ending NULL character. 
    
 _u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblLabel** macro lets you define a display table label when the number of characters in the label is known. The new structure is created with the following members: 
  
```
DTBLLABEL dtbllabel;
TCHAR lpszLabelName[n];

```

To use a pointer to the resulting structure from the **SizedDtblLabel** macro as a **DTBLLABEL** structure pointer, perform the following cast: 
  
```
lpDtblLabel = (LPDTBLLABEL) &amp;SizedDtblLabel;

```

## See also

#### Reference

[DTBLLABEL](dtbllabel.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

