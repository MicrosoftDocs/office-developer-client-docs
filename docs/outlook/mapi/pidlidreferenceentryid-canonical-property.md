---
title: "PidLidReferenceEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidReferenceEntryId
api_type:
- COM
ms.assetid: 42e7c3ac-1a04-4e3f-bf99-ef3f8fc45892
description: "Last modified: March 09, 2015"
---

# PidLidReferenceEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the reference [ENTRYID](entryid.md) for the contact. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidReferenceEID  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085BD  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

If present, this property should be equal to the value of the **EntryId** of the contact. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definition and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

