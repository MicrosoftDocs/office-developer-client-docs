---
title: "DTBLMVLISTBOX"
description: "DTBLMVLISTBOX describes a multi-valued list that will be displayed in a dialog box that is built from a display table."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTBLMVLISTBOX
api_type:
- COM
ms.assetid: 1c22f842-d0e7-44f0-a7d5-c9c2aa6b8820
---

# DTBLMVLISTBOX

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a multi-valued list that will be displayed in a dialog box that is built from a display table.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _DTBLMVLISTBOX
{
  ULONG ulFlags;
  ULONG ulMVPropTag;
} DTBLMVLISTBOX, FAR * LPDTBLMVLISTBOX;

```

## Members

 **ulFlags**
  
> Reserved; must be zero.
    
 **ulMVPropTag**
  
> Property tag for a multi-valued property of type PT_MV_TSTRING.
    
## Remarks

A **DTBLMVLISTBOX** structure describes a standard multi-valued list that has a read-only list of items. By using a standard multi-valued list, the values are displayed immediately. 
  
The data that is displayed comes from the property identified in the **ulMVPropTag** member. There is no requirement to read from the property interface that is associated with the display table. Also, because users are not able to make selections from these types of lists, data is not written to the property interface. 
  
Only multi-valued string properties are supported for the multi-valued list; other multi-valued property types are not supported. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

