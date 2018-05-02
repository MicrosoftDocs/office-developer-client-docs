---
title: "SizedDtblComboBox"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblComboBox
api_type:
- COM
ms.assetid: 1e5ea9f2-1029-4584-845a-890d3e956036
description: "Last modified: March 09, 2015"
---

# SizedDtblComboBox

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Creates a named structure that includes a [DTBLCOMBOBOX](dtblcombobox.md) structure for describing a combo box control and the maximum number of characters that can be entered in the associated edit control. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLCOMBOBOX** <br/> |
   
```
SizedDtblComboBox (n, u)
```

## Parameters

 _n_
  
> Number of characters that can be entered in the combo box's edit control. 
    
 _u_
  
> Name for the new structure.
    
## Remarks

The **SizedDtblComboBox** macro lets you define a combo box when the length of the enabled character string is known. The new structure is created with the following members: 
  
```
DTBLCOMBOBOX dtblcombobox;
TCHAR lpszCharsAllowed[n];

```

To use a pointer to the resulting structure from the **SizedDtblComboBox** macro as a **DTBLCOMBOBOX** structure pointer, perform the following cast: 
  
```
lpDtblComboBox = (LPDTBLCOMBOBOX) &amp;SizedDtblComboBox;

```

## See also

#### Reference

[DTBLCOMBOBOX](dtblcombobox.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

