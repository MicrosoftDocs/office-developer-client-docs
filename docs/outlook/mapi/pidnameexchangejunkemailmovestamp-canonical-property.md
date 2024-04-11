---
title: "PidNameExchangeJunkEmailMoveStamp Canonical Property"
description: Outlines the PidNameExchangeJunkEmailMoveStamp canonical property, which is stamped on every message that is moved by the Junk E-Mail Rule or is trusted.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidNameExchangeJunkEmailMoveStamp
api_type:
- COM
ms.assetid: 7a52f46c-371c-46d0-8d66-e154482e8269
---

# PidNameExchangeJunkEmailMoveStamp Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the persisted message value that indicates that the message should not be processed by a spam filter because the message was either already processed or is safe.
  
|Property |Value |
|:-----|:-----|
|Friendly names:  <br/> |None  <br/> |
|Property set:  <br/> |PS_PUBLIC_STRINGS  <br/> |
|Property name:  <br/> |http://schemas.microsoft.com/exchange/junkemailmovestamp  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Secure messaging  <br/> |
   
## Remarks

This property is stamped on every message that is moved by the Junk E-Mail Rule or is otherwise trusted content.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXCSPAM]](https://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk email messages.
    
[[MS-OXORSS]](https://msdn.microsoft.com/library/53bc9634-0040-4b5a-aecd-29781d826009%28Office.15%29.aspx)
  
> Specifies the properties and operations that represent RSS items.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

