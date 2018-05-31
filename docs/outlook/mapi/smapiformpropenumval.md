---
title: "SMAPIFormPropEnumVal"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SMAPIFormPropEnumVal
api_type:
- COM
ms.assetid: 694d40e9-cff2-435e-ad90-446044c306d2
description: "Last modified: March 09, 2015"
---

# SMAPIFormPropEnumVal

  
  
**Applies to**: Outlook 
  
Maps an enumerated integer value to a display name for that value. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
   
```cpp
typedef struct _SMAPIFormPropEnumVal
{
  LPSTR pszDisplayName;
  ULONG nVal;
} SMAPIFormPropEnumVal;

```

## Members

 **pszDisplayName**
  
> String that contains the display name for the value specified in the **nVal** member. 
    
 **nVal**
  
> An enumeration value for the display name pointed to by the **pszDisplayName** member. 
    
## Remarks

When a user selects a display name from a form, the name's corresponding enumeration value is stored by using the [IMAPIProp](imapipropiunknown.md) interface implementation that is associated with the form. 
  
## See also



[SMAPIFormProp](smapiformprop.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

