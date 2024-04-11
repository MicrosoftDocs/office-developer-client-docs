---
title: "DTBLMVDDLBOX"
description: "DTBLMVDDLBOX describes a drop-down list that will be used in a dialog box that is built from a display table."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTBLMVDDLBOX
api_type:
- COM
ms.assetid: 0e6283dc-9a08-460f-9400-03f0ceb4081c
---

# DTBLMVDDLBOX

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a drop-down list that will be used in a dialog box that is built from a display table.
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _DTBLMVDDLBX
{
  ULONG ulFlags;
  ULONG ulMVPropTag;
} DTBLMVDDLBX, FAR * LPDTBLMVDDLBX;

```

## Members

 **ulFlags**
  
> Reserved; must be zero.
    
 **ulMVPropTag**
  
> Property tag for a multi-valued property of type PT_MV_TSTRING. The different values of this property are displayed as distinct entries in the drop-down list.
    
## Remarks

A **DTBLMVDDLBOX** structure describes a multi-valued drop-down list a read-only list of items. By using a multi-valued drop-down list, values are displayed when a user clicks on a scroll bar. 
  
The data that is displayed comes from the property identified in the **ulMVPropTag** member. There is no requirement to read from the property interface that is associated with the display table. Also, because users are not able to make selections from these types of list boxes, data is not written to the property interface. 
  
Only multi-valued string properties are supported for the multi-valued drop-down list; other multi-valued property types are not supported. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

