---
title: "SizedDtblButton"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SizedDtblButton
api_type:
- COM
ms.assetid: ee73ced9-14d8-4a30-9b9f-d54ed9c3a454
description: "Last modified: March 09, 2015"
---

# SizedDtblButton

  
  
**Applies to**: Outlook 
  
Creates a named structure that includes a [DTBLBUTTON](dtblbutton.md) structure for describing a button and a label of a specified length. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLBUTTON** <br/> |
   
```
SizedDtblButton (n, u)
```

## Parameters

 _n_
  
> Length of the label to be included in the new structure.
    
 _u_
  
> Name for the new structure.
    
## Remarks

The new structure is created with the following members:
  
```
DTBLBUTTON dtblbutton;
TCHAR lpszLabel[n];

```

## See also

#### Reference

[DTBLBUTTON](dtblbutton.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

