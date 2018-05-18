---
title: "PidTagProviderIcon Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagProviderIcon
api_type:
- COM
ms.assetid: 59c84b1f-13b5-484b-b703-2fb9fcc6c7eb
description: "Last modified: March 09, 2015"
---

# PidTagProviderIcon Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a Unicode string that specifies a custom icon or icons to be displayed for a MAPI provider in the Microsoft Office Outlook status bar in both online and offline states.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_ICON, PR_PROVIDER_ICON_W  <br/> |
|Identifier:  <br/> |0x3417  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |MAPI message store  <br/> |
   
## Remarks

These properties specify the resource file that contains a custom icon that represents a MAPI provider in an online state, and optionally, another custom icon in the offline state. Outlook always requests these properties in Unicode representation. 
  
For example, the following property value instructs Outlook to load icon ID 1001 from the module mymod32.dll and use that icon for the online state:  `mymod32.dll,#1001`. Since there is no provider-specific icon for the offline state, in this case, the standard Outlook offline icon is used in the status bar. 
  
The following property value instructs Outlook to load icon ID 1001 from the module mymod32.dll and use that icon for the online state, and to also load icon ID 1002 from this same module to be used for the offline state:  `mymod32.dll,#1001,#1002`. No Outlook icon is used in the status bar. 
  
By default, if no custom icons are specified, the provider is represented by the Outlook default icons for the online state and the offline state. The provider can optionally specify a display name to be shown adjacent to the icon in the status bar. For more information, see **PR_PROVIDER_DISPLAY_NAME_W** ([PidTagProviderDisplayName](pidtagproviderdisplayname-canonical-property.md)).
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

