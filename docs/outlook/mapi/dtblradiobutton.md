---
title: "DTBLRADIOBUTTON"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLRADIOBUTTON
api_type:
- COM
ms.assetid: 64cef938-ef6f-43bb-8f6e-d4cd4d6c9888
description: "Last modified: March 09, 2015"
---

# DTBLRADIOBUTTON

  
  
**Applies to**: Outlook 
  
Describes one radio button that will be part of a radio button group. The radio button group will be used in a dialog box that is built from a display table.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _DTBLRADIOBUTTON
{
  ULONG ulbLpszLabel;
  ULONG ulFlags;
  ULONG ulcButtons;
  ULONG ulPropTag;
  long lReturnValue;
} DTBLRADIOBUTTON, FAR *LPDTBLRADIOBUTTON;

```

## Members

 **ulbLpszLabel**
  
> Position in memory of the character string label for the radio button.
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the label pointed to by the **ulbLpszLabel** member. The following flag can be set: 
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
 **ulcButtons**
  
> Count of buttons in the radio button group. The **DTBLRADIOBUTTON** structures for the other buttons in the group must be contained in successive rows of the display table. Each of these rows should contain the same value for the **ulcButtons** member. 
    
 **ulPropTag**
  
> Property tag for a property of type PT_LONG. The initial selection in the radio button group is based on the initial value of this property. Each button in the group must have **ulPropTag** set to the same property. 
    
 **lReturnValue**
  
> Unique number that identifies the selected button.
    
## Remarks

A **DTBLRADIOBUTTON** structure describes a radio button a button control that is associated with a group of buttons. Only one button in the group can be checked; setting one button causes the other buttons in the group to be unset. 
  
The button count is the number of radio buttons in the group. The structures for the other radio buttons in the group must be in subsequent rows in the display table. Each of these structures should have the same value for its button count.
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also

#### Reference

[BuildDisplayTable](builddisplaytable.md)
  
[DTCTL](dtctl.md)
  
[SizedDtblButton](sizeddtblbutton.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

