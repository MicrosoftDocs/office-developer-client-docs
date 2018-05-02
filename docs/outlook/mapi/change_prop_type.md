---
title: "CHANGE_PROP_TYPE"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.CHANGE_PROP_TYPE
api_type:
- COM
ms.assetid: 95513b5a-fd3b-46f2-a6c0-094500ae4ca7
description: "Last modified: March 09, 2015"
---

# CHANGE_PROP_TYPE

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Updates the property type of a property tag to a specified value. The property identifier is unchanged. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```
CHANGE_PROP_TYPE (ulPropTag, ulPropType)
```

## Parameters

 _ulPropTag_
  
> The property tag to be modified.
    
 _ulPropType_
  
> The new value for the property type.
    
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

