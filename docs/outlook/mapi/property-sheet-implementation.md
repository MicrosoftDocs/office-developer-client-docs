---
title: "Property Sheet Implementation"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f3475206-0237-4b5b-8efd-abd5d5e0b6c3
description: "Last modified: July 23, 2011"
 
 
---

# Property Sheet Implementation

  
  
**Applies to**: Outlook 
  
A property sheet is a dialog box for displaying the properties of an object. The properties can be read-only, enabling the user only to view them, or read/write, enabling the user to make changes. A property sheet contains one or more overlapping child windows called pages. Each page contains control windows for setting a group of related properties. Users navigate from page to page by selecting a tab that brings the corresponding page to the foreground of the property sheet.
  
Service providers must implement a property sheet that displays a minimal set of properties related to configuration in the message service. If you allow these message service properties to be changed, you can either allow users of client applications, such as the Control Panel, to make the changes or implement the changes programmatically. Implementing property sheets to display and edit other types of properties is optional. 
  
Typically, you will need to display a property sheet in the following situations:
  
- When a client calls your status object's [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method. 
    
- When MAPI calls your provider object's logon method.
    
- When MAPI calls the entry point function for your provider's message service.
    
Transport providers also implement property sheets to display properties related to message options, and address book providers implement property sheets to view and edit detailed information about messaging users and distribution lists, advanced search criteria, and templates for entering new users.
  
You can use one of the following three techniques to create a property sheet:
  
- Manually, as you would any dialog box.
    
- By using the property sheet common control provided in the Windows SDK.
    
- By using a MAPI display table.
    
Providers should choose the last option (create a property sheet by using a display table). This is the simplest option because it eliminates the need to work with the Windows user interface. 
  
To implement a property sheet built from a display table for your message service properties, use the following procedure:
  
1. Call [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) to open a section in the current profile. Pass your [MAPIUID](mapiuid.md) or NULL to open your provider's profile section. 
    
2. Call [CreateIProp](createiprop.md) to create a property data object. 
    
3. Call the profile section's [IMAPIProp::CopyTo](imapiprop-copyto.md) method to copy all of the section's properties to the property data object. 
    
4. Create a display table either by building one or more [DTPAGE](dtpage.md) structures that describe the controls to appear on the property sheet and calling the [BuildDisplayTable](builddisplaytable.md) function, or by implementing custom code. 
    
5. Call [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) to display a property sheet that has the copied properties. Pass a pointer to the property data object as the  _lpConfigData_ parameter and a pointer to the display table as the  _lpDisplayTable_ parameter. If you want to override the default access mode for this property sheet, do not set the DT_EDITABLE flag for each control in the display table that represents a read-only property. 
    
6. When all of the changes have been made in the property sheet, call the property data object's **IMAPIProp::CopyTo** method to copy the changed properties back to the profile section. 
    
For an overview of display tables, see [Display Tables](display-tables.md). 
  
For detailed information about display tables, see [Display Table Implementation](display-table-implementation.md). 
  
For information about implementing a control, see [Control Object Implementation](control-object-implementation.md).
  
To retrieve the index of a control that a user selects in a display table list box, wait until the user clicks **OK** or **Apply**. At this point, the entry identifier of the selected item is written back to the [IMAPIProp : IUnknown](imapipropiunknown.md) interface as the value of the property specified by the **ulPRSetProperty** member in the [DTBLLBX](dtbllbx.md) structure. 
  
If you need to be able to add or remove items from your list box, using a display table and the [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) method will not work. Instead, consider implementing a property sheet with the Win32 property sheet API contained in the comdlg32.dll file. 
  
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

