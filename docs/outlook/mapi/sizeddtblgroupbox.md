---
title: "SizedDtblGroupBox"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblGroupBox
api_type:
- COM
ms.assetid: 7ca01bf7-5185-41cc-907e-01f256345997
description: "Last modified: March 09, 2015"
---

# SizedDtblGroupBox

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a named structure that includes a [DTBLGROUPBOX](dtblgroupbox.md) structure for describing a group box control and a label of a specified length. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLGROUPBOX** <br/> |
   
```
SizedDtblGroupBox (n, u)
```

## Parameters

 _n_
  
> Length of the group box's label. 
    
 _u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblGroupBox** macro lets you define a group box control when the length of the label is known. The new structure is created with the following members: 
  
```
DTBLGROUPBOX dtblgroupbox;
TCHAR lpszLabel[n];

```

To use a pointer to the resulting structure from the **SizedDtblGroupBox** macro as a **DTBLGROUPBOX** structure pointer, perform the following cast: 
  
```
lpDtblGroupBox = (LPDTBLGROUPBOX) &amp;SizedDtblGroupBox;

```

## See also

#### Reference

[DTBLGROUPBOX](dtblgroupbox.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

