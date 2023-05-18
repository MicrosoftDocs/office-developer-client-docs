---
title: "DTBLLABEL"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTBLLABEL
api_type:
- COM
ms.assetid: 5837facf-acd3-48fe-9610-f88085d99aef
description: "Describes a label that will be used in a dialog box that is built from a display table."
---

# DTBLLABEL

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a label that will be used in a dialog box that is built from a display table.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro  <br/> |[SizedDtblLabel](sizeddtbllabel.md) <br/> |
   
```cpp
typedef struct _DTBLLABEL
{
  ULONG ulbLpszLabelName;
  ULONG ulFlags;
} DTBLLABEL, FAR *LPDTBLLABEL;

```

## Members

 **ulbLpszLabelName**
  
> Position in memory of the character string label.
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the label pointed to by the **ulbLpszLabelName** member. The following flag can be set: 
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
## Remarks

A **DTBLLABEL** structure describes a label control text that is displayed with another type of control to add meaning to that control. For example, most edit controls are positioned next to labels to inform the user of the type of information to be entered. Some controls, such as group boxes and radio buttons, hold their own labels. 
  
The label can include a Windows accelerator, identified as the character following the ampersand (&amp;). Pressing the accelerator key puts the focus in the first nonlabel, nonbutton control following this label in the display table.
  
There is no support for multiline labels. Showing multiple lines requires multiple labels.
  
It is not possible to use a label as a read-only edit control. The difference is that an edit control can be selected and copied whereas a label cannot. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

