---
title: "MVI_PROP"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.MVI_PROP
api_type:
- COM
ms.assetid: d7f07524-6935-4a60-aaf3-3f753ea8d86a
description: "Last modified: March 09, 2015"
---

# MVI_PROP

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the MVI_FLAG for a specified property. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```cpp
MVI_PROP (tag)
```

## Parameters

 _tag_
  
> The property tag to be modified.
    
## Remarks

The MVI_FLAG combines the setting of MV_FLAG, identifying a property as multi-valued, and MV_INSTANCE, requesting that a multi-valued property be displayed in a table in multiple rows. The property type of the affected property is modified, but the identifier remains unchanged. 
  
For example, when the MVI_PROP macro is applied to a property of type PT_FLOAT, its type is changed to PT_MV_FLOAT. When included in a table, multiple rows are used to represent the property that has one row for each value. The properties for the other columns are repeated. 
  
For more information about these flags, see [MAPI Property Type Overview](mapi-property-type-overview.md) and [Working with Multivalued Columns](working-with-multivalued-columns.md).
  
## See also



[SPropValue](spropvalue.md)


[Macros Related to Structures](macros-related-to-structures.md)

