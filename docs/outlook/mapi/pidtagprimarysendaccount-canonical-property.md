---
title: "PidTagPrimarySendAccount Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagPrimarySendAccount
api_type:
- COM
ms.assetid: 2f268b3b-2e4c-4aea-8879-bdd0ac1df35c
description: "Last modified: March 09, 2015"
---

# PidTagPrimarySendAccount Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a string that names the first server that is used to send the message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PRIMARY_SEND_ACCOUNT  <br/> |
|Identifier:  <br/> |0x0E28  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Account  <br/> |
   
## Remarks

Specifies the first server that a client should use to send the mail. The format of these properties is implementation dependent. These properties can be used by the client to determine which server to direct the mail through, but is optional and the value has no meaning to the server.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
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

