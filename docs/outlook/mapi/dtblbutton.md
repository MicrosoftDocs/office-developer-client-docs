---
title: "DTBLBUTTON"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLBUTTON
api_type:
- COM
ms.assetid: 6058c78b-05d4-45a3-988c-1fbf8322125e
description: "Last modified: March 09, 2015"
---

# DTBLBUTTON

  
  
**Applies to**: Outlook 
  
Contains information about a button control for a dialog box built from a display table.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[SizedDtblButton](sizeddtblbutton.md) <br/> |
   
```cpp
typedef struct _DTBLBUTTON
{
  ULONG ulbLpszLabel;
  ULONG ulFlags;
  ULONG ulPRControl;
} DTBLBUTTON, FAR *LPDTBLBUTTON;

```

## Members

 **ulbLpszLabel**
  
> Position in memory of the character string that is displayed on the button.
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the label pointed to by the **ulbLpszLabel** member. The following flag can be set: 
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
 **ulPRControl**
  
> Property tag for a property of type PT_OBJECT that implements the [IMAPIControl](imapicontroliunknown.md) interface. When the button is clicked, MAPI calls the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method for the display table's [IMAPIProp](imapipropiunknown.md) implementation to retrieve this property. 
    
## Remarks

A **DTBLBUTTON** structure describes a button a control that, when clicked, allows a user to begin an operation. Typically, clicking a button causes a modal dialog box to be displayed or a programmatic task to be invoked. Service providers can implement anything through a button control. If the button is supposed to perform a task based on the values of other controls, those controls must have set the DT_SET_IMMEDIATE flag. 
  
The **ulbLpszLabel** member is the position in memory of the character string that is displayed on the button. Service providers can add an ampersand character (&amp;) to indicate a Windows accelerator in the button label. Pressing an accelerator key has the same effect as clicking the button. 
  
The **ulPRControl** member describes an object property that, when opened with the **IMAPIProp::OpenProperty** method, returns a pointer to a control object. Implementing a control object that supports the **IMAPIControl** interface is a way to extend the MAPI feature set and define the operation or task that occurs when the button is clicked. **IMAPIControl** supplies two methods for manipulating buttons: [GetState](imapicontrol-getstate.md) to disable or enable buttons and [Activate](imapicontrol-activate.md) to handle button clicks. 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

