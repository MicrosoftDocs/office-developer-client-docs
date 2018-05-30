---
title: "SPropProblem"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SPropProblem
api_type:
- COM
ms.assetid: 55943197-fd11-442d-bb4b-0bff565b846e
description: "Last modified: March 09, 2015"
---

# SPropProblem

  
  
**Applies to**: Outlook 
  
Describes an error that relate to an operation involving a property.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SPropProblem
{
  ULONG ulIndex;
  ULONG ulPropTag;
  SCODE scode;
} SPropProblem, FAR *LPSPropProblem;

```

## Members

 **ulIndex**
  
> An index in an array of property tags.
    
 **ulPropTag**
  
> Property tag for the property that has the error.
    
 **scode**
  
> Error value describing the problem with the property. This value can be any MAPI [SCODE](scode.md) value. 
    
## Remarks

An array of **SPropProblem** structures is returned from the following methods: 
  
- [IMAPISupport::DoCopyTo](imapisupport-docopyto.md)
    
- [IMAPISupport::DoCopyProps](imapisupport-docopyprops.md)
    
- [IMAPIProp::DeleteProps](imapiprop-deleteprops.md)
    
- [IMAPIProp::SetProps](imapiprop-setprops.md)
    
- [IMAPIProp::CopyProps](imapiprop-copyprops.md)
    
- [IMAPIProp::CopyTo](imapiprop-copyto.md)
    
- [IPropData::HrAddObjProps](ipropdata-hraddobjprops.md)
    
An **SPropProblem** structure contains an **SCODE** error value that results from an operation trying to modify or delete a MAPI property. 
  
For more information about how the **SPropProblem** structure works with errors related to properties, see [MAPI Named Properties](mapi-named-properties.md). 
  
## See also



[SCODE](scode.md)
  
[SPropProblemArray](spropproblemarray.md)


[MAPI Structures](mapi-structures.md)

