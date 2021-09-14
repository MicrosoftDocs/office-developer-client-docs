---
title: "PidLidInternetAccountName Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidInternetAccountName
api_type:
- COM
ms.assetid: 29bedadf-903d-419d-804d-dc8bd92b745d
description: "Last modified: March 09, 2015"
---

# PidLidInternetAccountName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the user-visible email account name through which the email message is sent.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidInetAcctName  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008580  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

The format of this string is implementation dependent. This property can be used by the client to determine which server to direct the mail to, but is optional and the value has no meaning to the server.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
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

