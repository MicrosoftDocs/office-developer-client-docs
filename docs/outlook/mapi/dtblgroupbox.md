---
title: "DTBLGROUPBOX"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLGROUPBOX
api_type:
- COM
ms.assetid: 5e444b62-d6b6-4cfc-8601-d34aa004c1e6
description: "Last modified: March 09, 2015"
---

# DTBLGROUPBOX

  
  
**Applies to**: Outlook 
  
Describes a group box control that will be used in a dialog box built from a display table.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[SizedDtblGroupBox](sizeddtblgroupbox.md) <br/> |
   
```cpp
typedef struct _DTBLGROUPBOX
{
  ULONG ulbLpszLabel;
  ULONG ulFlags;
} DTBLGROUPBOX, FAR *LPDTBLGROUPBOX;

```

## Members

 **ulbLpszLabel**
  
> Position in memory of the character string that accompanies the group box. If displayed, the label appears on the top, left-hand side of the box.
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the label pointed to by the **ulbLpszLabel** member. The following flag can be set: 
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
## Remarks

A **DTBLGROUPBOX** structure describes a group box control that is used to visually associate other controls in the dialog box. The highlighting technique involves surrounding the other controls by a box. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

