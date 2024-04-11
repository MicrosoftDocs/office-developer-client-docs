---
title: "Control Object Implementation"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 4ad62ff0-c527-4e75-a2af-b5906a7588e8 
---

# Control Object Implementation

**Applies to**: Outlook 2013 | Outlook 2016
  
Control objects, or objects that support the [IMAPIControl : IUnknown](imapicontroliunknown.md) interface, are implemented by providers to add functionality to a button that appears on a MAPI dialog box. Control objects can only be implemented for buttons.
  
 **IMAPIControl** has three methods: [GetLastError](imapicontrol-getlasterror.md), [GetState](imapicontrol-getstate.md), and [Activate](imapicontrol-activate.md).
  
MAPI calls **GetState** to determine whether or not to disable the button. **GetState** is called in the following situations:
  
- When the dialog box on which the button appears is first displayed.

- When a display table notification is issued for the button.

Set the contents of the _lpulState_ parameter to MAPI_DISABLED if the user cannot interact with the button and MAPI_ENABLED if the user can interact.
  
When the user clicks the button, MAPI calls **Activate**. **Activate** performs the task that has been associated with the button. This task can be anything appropriate for your provider, such as displaying a dialog box or updating a property. If the task is unsuccessful because the user canceled it, return MAPI_E_USER_CANCEL. For other causes of failure, return the appropriate error value.
  
If the task is successful and it is linked to a property change that is reflected in another control on the dialog box, call [ITableData::HrNotify](itabledata-hrnotify.md). **HrNotify** is called to issue a display table notification with the changed property's **PR_CONTROL_ID** ([PidTagControlId](pidtagcontrolid-canonical-property.md)) property in the [TABLE_NOTIFICATION](table_notification.md) structure. Do not place the new property value in the structure; instead, return it when [IMAPIProp::GetProps](imapiprop-getprops.md) is called. Although typically a display table notification cannot be used to disable or enable a control, it can be used with a button. MAPI will refresh the changed control to respond to the notification.
  
MAPI calls the control's **GetLastError** method when **Activate** returns an error other than MAPI_E_USER_CANCEL. If **GetLastError** places extended error information in the [MAPIERROR](mapierror.md) structure that it returns in the contents of the_lppMAPIError_ parameter, MAPI displays it for the user.
  
## See also

[MAPI Service Providers](mapi-service-providers.md)
