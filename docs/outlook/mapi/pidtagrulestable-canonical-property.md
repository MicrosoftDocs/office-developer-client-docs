---
title: "PidTagRulesTable Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: fc520720-8190-4dff-8f6c-1bebf7080b57
description: "Contains a table with all rules applied to a folder. This property is present on all folder objects on an Exchange Server that have rules."
---

# PidTagRulesTable Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a table with all rules applied to a folder.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RULES_TABLE  <br/> |
|Identifier:  <br/> |0x3FE1  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |Server Side Rules  <br/> |
   
## Remarks

This property is present on all folder objects on an Exchange Server that have rules. Values included in this property are used for reading and modifying rules. You can use the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method with the **IID_IExchangeModifyTable** interface identifier to obtain an [IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md) interface to the rules table on a folder. You can use this interface to read and modify those rules. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties. 
    
## See also



[IExchangeModifyTable : IUnknown](iexchangemodifytableiunknown.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

