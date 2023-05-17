---
title: "PidTagDisplayName Canonical Property"
description: Outlines the PidTagDisplayName canonical property, which contains the display name for a given MAPI object. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDisplayName
api_type:
- HeaderDef
ms.assetid: bd094e00-5c60-4bb3-9a45-b943fab52876
---

# PidTagDisplayName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the display name for a given MAPI object. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_DISPLAY_NAME, PR_DISPLAY_NAME_A, PR_DISPLAY_NAME_W  <br/> |
|Identifier:  <br/> |0x3001  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

Folders require sibling subfolders to have unique display names. For example, if a folder contains two subfolders, the two subfolders cannot use the same value for this property. This restriction does not apply to other containers, such as address books and distribution lists. 
  
Service providers should set the value of this property so that it contains both the provider type and configuration information. The additional information helps to distinguish between instances of providers of the same type. Unconfigured providers should use a string that names the provider. Configured providers should use the same string followed by a distinguishing string in parentheses. For example, an unconfigured message store provider might set these properties to: 
  
Personal Information Store
  
The configured version could then set these properties to: 
  
Personal Information Store (February 6, 1998)
  
For status objects, these properties contain the name of the component that can be displayed by the user interface. 
  
> [!NOTE]
> Semicolons cannot be used within recipient names in MAPI messaging. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXCFOLD]](https://msdn.microsoft.com/library/c0f31b95-c07f-486c-98d9-535ed9705fbf%28Office.15%29.aspx)
  
> Handles folder operations.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-OXCMAIL]](https://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
[[MS-XWDVSEC]](https://msdn.microsoft.com/library/dc043d09-6b76-4392-aea3-68f8e81c64d8%28Office.15%29.aspx)
  
> Extends the WebDAV protocol that specifies how to request and set the Exchange security descriptor via WebDAV methods.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagTransmittableDisplayName Canonical Property](pidtagtransmittabledisplayname-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

