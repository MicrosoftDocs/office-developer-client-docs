---
title: "SizedDtblButton"
description: Outlines SizedDtblButton, which creates a named structure that includes a DTBLBUTTON structure for describing a button and a label of a specified length. 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SizedDtblButton
api_type:
- COM
ms.assetid: ee73ced9-14d8-4a30-9b9f-d54ed9c3a454
---

# SizedDtblButton

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a named structure that includes a [DTBLBUTTON](dtblbutton.md) structure for describing a button and a label of a specified length. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |**DTBLBUTTON** <br/> |
   
```cpp
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



[DTBLBUTTON](dtblbutton.md)


[Macros Related to Structures](macros-related-to-structures.md)

