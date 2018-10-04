---
title: "PidLidInternetAccountStamp Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidInternetAccountStamp
api_type:
- COM
ms.assetid: 819179fe-e58e-415c-abc7-1949036745ee
description: "Last modified: March 09, 2015"
---

# PidLidInternetAccountStamp Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the email account ID through which the email message is sent.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidInetAcctStamp  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008581  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

The format of this string is implementation dependent. This property can be used by the client to determine which server to direct the mail to, but is optional and the value has no meaning to the server.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

