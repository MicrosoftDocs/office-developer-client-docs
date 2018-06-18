---
title: "DTBLCHECKBOX"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.DTBLCHECKBOX
api_type:
- COM
ms.assetid: 0dd12990-5431-4768-9d64-27d4ef6b7b20
description: "Last modified: March 09, 2015"
---

# DTBLCHECKBOX

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains information about a check box that will be used in a dialog box built from a display table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macro:  <br/> |[SizedDtblCheckBox](sizeddtblcheckbox.md) <br/> |
   
```cpp
typedef struct _DTBLCHECKBOX
{
  ULONG ulbLpszLabel;
  ULONG ulFlags;
  ULONG ulPRPropertyName;
} DTBLCHECKBOX, FAR *LPDTBLCHECKBOX;

```

## Members

 **ulbLpszLabel**
  
> Position in memory of the character string that is displayed with the check box. 
    
 **ulFlags**
  
> Bitmask of flags used to designate the format of the check box label. The following flag can be set:
    
MAPI_UNICODE 
  
> The label is in Unicode format. If the MAPI_UNICODE flag is not set, the label is in ANSI format.
    
 **ulPRPropertyName**
  
> Property tag for a property of type PT_BOOLEAN. The value of this property is affected by the state of the check box.
    
## Remarks

A **DTBLCHECKBOX** structure describes a check box a control that reflects one of two states: enabled (a checked box) or disabled (an empty box). 
  
The **ulPRPropertyName** member describes a Boolean property whose value is manipulated by changing the state of the check box. When the check box is first displayed, MAPI calls the **GetProps** method of the **IMAPIProp** implementation that is associated with the display table to retrieve a set of default properties. If one of the properties maps to the property tag in the **DTBLCHECKBOX** structure, the value for that property is displayed as the check box's initial value. 
  
Check box controls can be modifiable. This allows a user to change their states. Modifiable check boxes set the DT_EDITABLE flag in the **ulCtlFlags** member of their [DTCTL](dtctl.md) structure and in their **PR_CONTROL_FLAGS** ([PidTagControlFlags](pidtagcontrolflags-canonical-property.md)) property. When a check box changes its state, MAPI calls [IMAPIProp::SetProps](imapiprop-setprops.md) to set the property identified in the property tag member of the **DTBLCHECKBOX** structure to the new state. 
  
For example, an address book provider might include a modifiable check box control in its configuration dialog box to adjust the setting of a recipient's **PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) property. When the user selects the check box, MAPI sets this property to TRUE. When the check box is unselected, the property is set to FALSE.
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md). For information about property types, see [MAPI Property Type Overview](mapi-property-type-overview.md).
  
## See also



[DTCTL](dtctl.md)
  
[PidTagControlType Canonical Property](pidtagcontroltype-canonical-property.md)


[MAPI Structures](mapi-structures.md)

