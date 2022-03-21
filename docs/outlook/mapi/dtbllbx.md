---
title: "DTBLLBX"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.DTBLLBX
api_type:
- COM
ms.assetid: 971b4837-6823-4f28-9803-3c22b2ec091f
description: "Describes a list that will be used in a dialog box that is built from a display table."
---

# DTBLLBX

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a list that will be used in a dialog box that is built from a display table.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _DTBLLBX
{
  ULONG ulFlags;
  ULONG ulPRSetProperty;
  ULONG ulPRTableName;
} DTBLLBX, FAR *LPDTBLLBX

```

## Members

 **ulFlags**
  
> Bitmask of flags used to eliminate a horizontal or vertical scroll bar from the list. The following flags can be set:
    
MAPI_NO_HBAR 
  
> No horizontal scroll bar should be shown with the list.
    
MAPI_NO_VBAR 
  
> No vertical scroll bar should be shown with the list.
    
 **ulPRSetProperty**
  
> Property tag for a property of any type. This property is one of the columns in the table identified by the **ulPRTableTable** member. 
    
 **ulPRTableName**
  
> Property tag for a table property of type PT_OBJECT that can be opened by using an **OpenProperty** call. The number of columns that the table should have depends on whether the list is a single or multiple selection list. If the **ulPRSetProperty** member is set to **PR_NULL** ([PidTagNull](pidtagnull-canonical-property.md)), the list allows for multiple selection.
    
## Remarks

A **DTBLLBX** structure describes a list a control that is used to show multiple items and let a user select one or more of the items. 
  
The **ulPRSetProperty** member and **ulPRTableName** member work together; when one value is chosen from the table, it is written back to **ulPRSetProperty** when the dialog box is dismissed. 
  
The flags value indicates whether a horizontal or vertical scroll bar should be displayed with the list. The default is to have types of scroll bars appear if it is required. Service providers can set MAPI_NO_HBAR to suppress a horizontal scroll bar and MAPI_NO_VBAR to suppress a vertical scroll bar. 
  
The two property tag members work together to display values in the list and set corresponding properties when an item in the list is selected. When MAPI first displays the list, it calls the **IMAPIProp** implementation's **OpenProperty** method to retrieve the table identified in the **ulPRTableName** member. The number of columns in the table depends on the value of the **ulPRSetProperty** member. If **ulPRSetProperty** is set to **PR_NULL**, the list is a multiple selection list based on an object that contains recipients, such as an address book container, a recipient table for a message, or a distribution list contents table. 
  
A table for a multiple selection list must include the following columns:
  
 **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
  
 **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))
  
 **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))
  
 **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) and a maximum of five other multivalued string properties can also be displayed with the three required columns. 
  
If the **ulPRSetProperty** member is not set to **PR_NULL**, the list is a single selection list. The initial value of **ulPRSetProperty** determines the first selected row. When a user selects one of the rows, the **ulPRSetProperty** member is set to the selected value and this value is written back to the property interface implementation with a call to [IMAPIProp::SetProps](imapiprop-setprops.md). 
  
For an overview of display tables, see [Display Tables](display-tables.md). For information about how to implement a display table, see [Implementing a Display Table](display-table-implementation.md).
  
## See also



[DTCTL](dtctl.md)


[MAPI Structures](mapi-structures.md)

