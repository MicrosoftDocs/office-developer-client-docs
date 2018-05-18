---
title: "FBadPropTag"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- FBadPropTag
api_type:
- HeaderDef
ms.assetid: 143bd3c6-5a55-4122-8522-9c48473aa781
description: "Last modified: March 09, 2015"
---

# FBadPropTag

  
  
**Applies to**: Outlook 
  
Validates a specified property tag. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapival.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
   
```cpp
ULONG FBadPropTag(
  ULONG ulPropTag
);
```

## Parameters

 _ulPropTag_
  
> [in] The property tag to be validated.
    
## Return value

TRUE 
  
> The specified property tag is not a valid MAPI property tag. 
    
FALSE 
  
> The specified property tag is a valid MAPI property tag.
    
## Remarks

The **FBadPropTag** function validates the specified property tag based on MAPI definitions. It make sures that the property type is one of the types defined by MAPI and that the property identifier is defined to be of that type. 
  
## See also



[FBadProp](fbadprop.md)

