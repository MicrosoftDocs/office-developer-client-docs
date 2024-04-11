---
title: "Display Tables"
description: "A display table describes how to show a type of dialog box — having one or more tabbed property pages dedicated to displaying or editing one or more properties."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c314ff6d-3e60-4b81-87ac-6ca6753ff633
 
 
---

# Display Tables

  
  
**Applies to**: Outlook 2013 | Outlook 2016
  
A display table describes how to show a specific type of dialog box — one having one or more tabbed property pages dedicated to displaying and possibly editing one or more properties. Associated with every display table is an [IMAPIProp : IUnknown](imapipropiunknown.md) interface implementation. The **IMAPIProp** implementation maintains the property data that is presented in the dialog box.
  
The rows in a display table represent the controls, or user interface objects, that are displayed in the dialog box. MAPI defines many types of controls, some with static values and some with dynamic values that a user can change. Most controls can be associated with properties maintained with the **IMAPIProp** implementation. When a user changes the value of a modifiable control, the corresponding property is updated.
  
Service providers implement display tables and the **IMAPIProp** interface. Creating a display table is similar to writing a program with a scripting language. Service providers can create a display table by:
  
- Calling the [BuildDisplayTable](builddisplaytable.md) function.

    - Or -

- Including custom code that populates the display table directly using a table data object — an object that supports the [ITableData : IUnknown](itabledataiunknown.md) interface.

The **BuildDisplayTable** function combines information from display table structures with visual elements from a dialog box resource to build display table rows. The function returns a pointer to an [IMAPITable : IUnknown](imapitableiunknown.md) interface implementation, and, if requested, a pointer to an **ITableData** interface implementation.
  
Using **BuildDisplayTable** to create a display table is straightforward and makes maintenance easier when visual elements of the display change. However, service providers that prefer not to use **BuildDisplayTable** can create a display table with custom code that uses the methods of **ITableData**. For example, service providers that have an existing template structure for their property pages might want to create custom code rather than use **BuildDisplayTable**.
  
There are a variety of ways service providers can implement the property interface for their display table. These include:
  
- Supplying a standard [IMAPIProp : IUnknown](imapipropiunknown.md) implementation.
    
- Supplying a wrapped **IMAPIProp** implementation that includes special processing before making the standard calls.
    
- Supplying an [IPropData : IMAPIProp](ipropdataimapiprop.md) implementation.
    
The type of implementation depends on the characteristics of the data to be displayed and the responsible service provider. For example, if there is an implicit relationship between the data in two edit controls and one of the controls changes, the **IMAPIProp** implementation must change the value of the other control appropriately.
  
Display tables have the following properties in their required column set:
  
||Value |
|:-----|:-----|
|**PR_XPOS** ([PidTagXCoordinate](pidtagxcoordinate-canonical-property.md))  <br/> |**PR_YPOS** ([PidTagYCoordinate](pidtagycoordinate-canonical-property.md))  <br/> |
|**PR_DELTAX** ([PidTagDeltaX](pidtagdeltax-canonical-property.md))  <br/> |**PR_DELTAY** ([PidTagDeltaY](pidtagdeltay-canonical-property.md))  <br/> |
|**PR_CONTROL_TYPE** ([PidTagControlType](pidtagcontroltype-canonical-property.md))  <br/> |**PR_CONTROL_FLAGS** ([PidTagControlFlags](pidtagcontrolflags-canonical-property.md))  <br/> |
|**PR_CONTROL_STRUCTURE** ([PidTagControlStructure](pidtagcontrolstructure-canonical-property.md))  <br/> |**PR_CONTROL_ID** ([PidTagControlId](pidtagcontrolid-canonical-property.md))  <br/> |

 **PR_XPOS** and **PR_YPOS** specify the X and Y coordinates of the upper left corner of the control. The horizontal units are 1/4 of the dialog base width unit; the vertical units are 1/8 of the dialog base height unit. Windows computes the current dialog base units from the height and width of the current system font. The coordinates are relative to the origin of the property page area. The size of property pages is limited to approximately 200 by 180 dialog units.
  
 **PR_DELTAX** and **PR_DELTAY** are the width and height of the control. These are ULONG values. The width units are 1/4 of the dialog base width unit; the height units are 1/8 of the dialog base height unit. The coordinates are relative to the origin of the control.
  
The other four properties describe various characteristics of the control. **PR_CONTROL_TYPE** indicates the type of control. MAPI defines twelve types of controls, each with a different set of attributes. These attributes are described in the flags property, **PR_CONTROL_FLAGS**. Examples of attributes include whether or not a control is editable or required.
  
The control structure, **PR_CONTROL_STRUCTURE**, contains information relevant to the particular type of control. Each type of control is described with a different structure. For example, edit controls are described with the [DTBLEDIT](dtbledit.md) structure. **DTBLEDIT** structures contain members that list the number of and specific types of characters that can be placed on the control and a property tag that identifies the property whose value is to be displayed in the control. **PR_CONTROL_STRUCTURE** is stored as a binary property.
  
The control identifier, **PR_CONTROL_ID**, uniquely identifies the control in the dialog box described by the display table. **PR_CONTROL_ID** is set from the values placed in the *lpbNotif* and *cbNotif* members of the [DTCTL](dtctl.md) structure that is used by **BuildDisplayTable** to create the display table. Because MAPI sometimes combines display tables, the identifier in **PR_CONTROL_ID** should always be unique. Typically, providers assign a [GUID](guid.md) structure to **PR_CONTROL_ID** to ensure its uniqueness. The **PR_CONTROL_ID** property is included in the [TABLE_NOTIFICATION](table_notification.md) structure when a display table notification is generated.
  
For more information about display tables, see [Display Table Implementation](display-table-implementation.md) and [About Display Table Notifications](about-display-table-notifications.md).
  
## See also

[MAPI Tables](mapi-tables.md)
