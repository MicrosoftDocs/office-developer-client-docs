---
title: "PidLidAddressBookProviderArrayType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAddressBookProviderArrayType
api_type:
- COM
ms.assetid: ca4eb6c2-98e9-4dbc-9f5a-f0f257456ead
description: "Last modified: March 09, 2015"
---

# PidLidAddressBookProviderArrayType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies the state of the contact's electronic addresses and represents a set of bit flags.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidABPArrayType  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008029  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

The value of the **dispidABPArrayType** property must be a combination of flags that specify the state of the contact object. Individual flags are specified in the following table. If this property is set, the **dispidABPEmailList** ([PidLidAddressBookProviderEmailList](pidlidaddressbookprovideremaillist-canonical-property.md)) property must be set, as well. These two properties must be kept synchronized with each other. For example, if **dispidABPArrayType** has the bit "0x00000001 set", one of the values of **dispidABPEmailList** must be "0x00000000". 
  
|**Bit**|**Description**|
|:-----|:-----|
|0x00000001  <br/> |Email1 is defined for the contact.  <br/> |
|0x00000002  <br/> |Email2 is defined for the contact.  <br/> |
|0x00000004  <br/> |Email3 is defined for the contact.  <br/> |
|0x00000008  <br/> |Business fax is defined for the contact.  <br/> |
|0x00000010  <br/> |Home fax is defined for the contact.  <br/> |
|0x00000020  <br/> |Primary fax is defined for the contact.  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](http://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

