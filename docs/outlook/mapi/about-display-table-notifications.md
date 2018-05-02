---
title: "About Display Table Notifications"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 085151e9-4809-4d2b-ae4d-e318355e1f5a
description: "Last modified: March 09, 2015"
 
 
---

# About Display Table Notifications

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Notifications on a display table are sent by the service provider responsible for creating the display table to MAPI. MAPI registers for these notifications by calling a display table's [IMAPITable::Advise](imapitable-advise.md) method and specifying the table modified event. 
  
As with all table notifications, display table notifications include a [TABLE_NOTIFICATION](table_notification.md) structure. Only the **ulTableEvent** and the **propIndex** members of this structure are significant; the other members are ignored. The **ulTableEvent** member is set to TABLE_ROW_MODIFIED and the **propIndex** member is set to the value of the **PR_CONTROL_ID** ( [PidTagControlId](pidtagcontrolid-canonical-property.md)) column in the corresponding row. MAPI responds to the notification by calling the [IMAPIProp::GetProps](imapiprop-getprops.md) method for the property displayed in the control and by displaying the new value. 
  
Display table notifications can be used by a service provider to coordinate changes to related controls on the dialog box. For example, if the property interface implementation needs to refresh one or more fields on the dialog box — perhaps in response to another control that has set the DT_SET_IMMEDIATE flag in its **PR_CONTROL_FLAGS** ( [PidTagControlFlags](pidtagcontrolflags-canonical-property.md)) property — it can generate a display table notification. A display table notification can alert the property interface implementation that the value of one or more controls needs to be reread due to a change being made or an external event occurring. 
  
A service provider can issue display table notifications by:
  
- Calling [ITableData::HrNotify](itabledata-hrnotify.md), if the display table was built with a table data object.
    
    - Or -
    
- Using its own code, if the display table was built with the provider's **IMAPITable** implementation. 
    
MAPI responds to display table notifications when necessary by rereading a control's value from the property interface implementation. The following table describes the details surrounding how MAPI handles notifications for specific types of controls.
  
|**Control**|**MAPI action**|
|:-----|:-----|
|Button  <br/> |Calls [IMAPIProp::OpenProperty](imapiprop-openproperty.md)to retrieve the control object by way of the property represented by the **ulPRControl** member of the [DTBLBUTTON](dtblbutton.md) structure if the call had failed previously. Calls the control object's [IMAPIControl::GetState](imapicontrol-getstate.md) to determine whether the button should be enabled and enables or disables the button accordingly.  <br/> |
|Check box  <br/> |Rereads the value for the **ulPRPropertyName** member.  <br/> |
|Combo box  <br/> |Reopens the table associated with the **ulPRTableName** member of the [DTBLCOMBOBOX](dtblcombobox.md) structure. Rereads all of the rows including the value for the **ulPRPropertyName**member.  <br/> |
|Drop-down list box  <br/> |Reopens the table associated with the **ulPRTableName** member of the [DTBLDDLBX](dtblddlbx.md) structure and rereads all of the rows. Calls [IMAPIProp::GetProps](imapiprop-getprops.md) to retrieve the values for the properties stored in the **ulPRDisplayProperty** and the **ulPRSetProperty** members.  <br/> |
|Edit  <br/> |Rereads the property and redisplays.  <br/> |
|Group box  <br/> |Ignores the notification.  <br/> |
|Label  <br/> |Ignores the notification.  <br/> |
|Multiple selection list box  <br/> |If one of the columns is an entry identifier, refreshes the list box. The corresponding object is not closed or reloaded.  <br/> |
|Single selection list box  <br/> |Reads the set property, trying to identify it.  <br/> |
|Multivalued list box  <br/> |Rereads the property and repopulates the list box.  <br/> |
|Tabbed page  <br/> |There are no notifications for this control; everything is static.  <br/> |
|Radio button  <br/> |Rereads the property that is associated with the button and is stored in the **ulPropTag** member of the [DTBLRADIOBUTTON](dtblradiobutton.md) structure and makes the appropriate selection with the controls.  <br/> |
   
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

