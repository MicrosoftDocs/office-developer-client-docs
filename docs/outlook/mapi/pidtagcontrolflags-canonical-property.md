---
title: "PidTagControlFlags Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagControlFlags
api_type:
- HeaderDef
ms.assetid: b97a9e72-fbb7-49ab-a19d-5e9bd1b8a80d
description: "Last modified: March 09, 2015"
---

# PidTagControlFlags Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a bitmask of flags governing the behavior of a control used in a dialog box built from a display table.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTROL_FLAGS  <br/> |
|Identifier:  <br/> |0x3F00  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI display table  <br/> |
   
## Remarks

One or more of the following flags can be set for this property:
  
DT_ACCEPT_DBCS 
  
> The control can have Double-Byte Character Set (DBCS) characters in it. This flag is used with edit controls. It allows multiple-byte character sets.
    
DT_EDITABLE 
  
> The control can be edited; the value associated with the control can be changed. When this flag is not set, the control is read-only. This value is ignored on label, group box, standard push button, multivalued drop down list box and list box controls.
    
DT_MULTILINE 
  
> The edit control can contain multiple lines. This means a return character can be entered within the control. This flag is valid for edit controls only.
    
DT_PASSWORD_EDIT 
  
> Applies to edit controls. The edit control is treated like a password. The value is displayed using asterisks instead of echoing the actual characters entered.
    
DT_REQUIRED 
  
> If the control allows changes (DT_EDITABLE), it must have a value before [IMAPIProp::SaveChanges](imapiprop-savechanges.md) is called. 
    
DT_SET_IMMEDIATE 
  
> Enables immediate setting of a value; as soon as a value in the control changes, MAPI calls the **SetProps** method for the property associated with that control. When this flag is not set, the values are set when the dialog box is dismissed. 
    
DT_SET_SELECTION 
  
> When a selection is made within the list box, the index column of that list box is set as a property. Always used with DT_SET_IMMEDIATE.
    
This property is stored in the ulCtlFlags member of a control's [DTCTL](dtctl.md) structure. Most of the control flags apply to all of the controls that allow user input; a few apply only to the edit control. Controls that do not allow user input, such as a button or a label, set 0 for their control flags. 
  
Many of the flag values are self-explanatory. For example, when DT_REQUIRED is set for a control, it must contain a value before the dialog box is allowed to be dismissed. Either the service provider can supply a value through its **IMAPIProp** implementation or the user can enter one. DT_EDITABLE indicates that the value for the control can be modified. DT_MULTILINE allows the value for an edit control to span multiple lines. 
  
Some control flags are not so obvious in their meaning. When a control sets the DT_SET_IMMEDIATE flag, any changes to its value take affect as soon as the user moves to a new control. MAPI makes a single call to the property interface's [IMAPIProp::SetProps](imapiprop-setprops.md) method for the control's property. This is different from the default behavior, which is to postpone having changes to control values take effect until after the user selects the **OK** button or dismisses the dialog box. The DT_SET_IMMEDIATE flag is often used in combination with display table notifications. 
  
The following table lists the types of controls and all of the flag values that can be set for each type.
  
|**Control**|**Valid values for this property**|
|:-----|:-----|
|Button  <br/> |Must be zero  <br/> |
|Check box  <br/> |DT_EDITABLE, DT_SET_IMMEDIATE  <br/> |
|Combo box  <br/> |DT_EDITABLE, DT_REQUIRED, DT_SET_IMMEDIATE  <br/> |
|Drop-down list box  <br/> |DT_EDITABLE, DT_SET_IMMEDIATE  <br/> |
|Edit  <br/> |DT_ACCEPT_DBCS, DT_MULTILINE, DT_EDITABLE, DT_PASSWORD_EDIT, DT_REQUIRED, DT_SET_IMMEDIATE  <br/> |
|Group box  <br/> |Must be zero  <br/> |
|Label  <br/> |Must be zero  <br/> |
|List box  <br/> |Must be zero  <br/> |
|Multivalue drop-down list box  <br/> |Must be zero  <br/> |
|Multivalue list box  <br/> |Must be zero  <br/> |
|Tabbed page  <br/> |Must be zero  <br/> |
|Radio button  <br/> |Must be zero  <br/> |
   
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

