---
title: "PidTagControlType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagControlType
api_type:
- HeaderDef
ms.assetid: 7728fa2f-4a59-4e86-90f1-4384824598aa
description: "Last modified: March 09, 2015"
---

# PidTagControlType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a value indicating a control type for a control used in a dialog box. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTROL_TYPE  <br/> |
|Identifier:  <br/> |0x3F02  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI display table  <br/> |
   
## Remarks

This property can have exactly one of the following values:
  
DTCT_BUTTON 
  
> A dialog button control.
    
DTCT_CHECKBOX 
  
> A dialog check box.
    
DTCT_COMBOBOX 
  
> A dialog combo box.
    
DTCT_DDLBX 
  
> A dialog drop-down list box.
    
DTCT_EDIT 
  
> A dialog edit text box.
    
DTCT_GROUPBOX 
  
> A dialog group box.
    
DTCT_LABEL 
  
> A dialog label.
    
DTCT_LBX 
  
> A dialog list box.
    
DTCT_LISTBOX 
  
> A dialog list box.
    
DTCT_MVDDLBX 
  
> A multivalued list box populated by a multivalued property of type string.
    
DTCT_PAGE 
  
> A dialog tabbed page.
    
DTCT_RADIOBUTTON 
  
> A dialog radio button.
    
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

