---
title: "STnefProblem"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.STnefProblem
api_type:
- COM
ms.assetid: 3fe651b7-0ddf-42fd-8277-9224505be1a8
description: "Last modified: March 09, 2015"
---

# STnefProblem

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains information about a property or attribute processing problem that occurred during the encoding or decoding of a Transport Neutral Encapsulation Format (TNEF) stream.
  
|||
|:-----|:-----|
|Header file:  <br/> |Tnef.h  <br/> |
   
```cpp
typedef struct _STnefProblem
{
  ULONG ulComponent;
  ULONG ulAttribute;
  ULONG ulPropTag;
  SCODE scode;
} STnefProblem;

```

## Members

 **ulComponent**
  
> The type of processing during which the problem occurred. If the problem occurred during message processing, the **ulComponent** member is set to zero. If the problem occurred during attachment processing, **ulComponent** is set equal to the corresponding attachment's **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) value.
    
 **ulAttribute**
  
> Attribute associated with the property indicated by the **ulPropTag** member or, when the TNEF processing problem occurs when decoding an encapsulation block, one of the following values: 
    
 _attMAPIProps_
  
> Message level
    
 _attAttachment_
  
> Attachment level
    
 **ulPropTag**
  
> Property tag of the property that caused the TNEF processing problem, except when the problem occurs when decoding an encapsulation block, in which case **ulPropTag** is set to zero. 
    
 **scode**
  
> Error value indicating the problem encountered during processing.
    
## Remarks

If an **STnefProblem** structure is not generated during the processing of an attribute or property, the application can continue under the assumption that the processing of that attribute or property succeeded. The only exception occurs when the problem arose during decoding of an encapsulation block. In this case, the decoding of the component corresponding to the block is stopped and decoding is continued in another component. 
  
## See also



[STnefProblemArray](stnefproblemarray.md)
  
[PidTagAttachNumber Canonical Property](pidtagattachnumber-canonical-property.md)


[MAPI Structures](mapi-structures.md)

