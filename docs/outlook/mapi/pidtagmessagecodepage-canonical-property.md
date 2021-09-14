---
title: "PidTagMessageCodepage Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageCodepage
api_type:
- HeaderDef
ms.assetid: eef73e34-470c-4c37-94ce-ea95fe83bc10
description: "Last modified: March 09, 2015"
---

# PidTagMessageCodepage Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the code page that is used for the message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_CODEPAGE  <br/> |
|Identifier:  <br/> |0x3FFD  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Common  <br/> |
   
## Remarks

The folder object code page is used if this property is set to zero (0).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXPFOAB]](https://msdn.microsoft.com/library/258a07a7-34a7-4373-87c1-cddf51447d00%28Office.15%29.aspx)
  
> Specifies the method of delivering offline address book (OAB) data from server to client.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

