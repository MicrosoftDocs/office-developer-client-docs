---
title: "CHANGE_PROP_TYPE"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.CHANGE_PROP_TYPE
api_type:
- COM
ms.assetid: 95513b5a-fd3b-46f2-a6c0-094500ae4ca7
description: "Last modified: March 09, 2015"
---

# CHANGE_PROP_TYPE

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Updates the property type of a property tag to a specified value. The property identifier is unchanged. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```cpp
CHANGE_PROP_TYPE (ulPropTag, ulPropType)
```

## Parameters

 _ulPropTag_
  
> The property tag to be modified.
    
 _ulPropType_
  
> The new value for the property type.
    
## See also



[SPropValue](spropvalue.md)


[Macros Related to Structures](macros-related-to-structures.md)

