---
title: "PidLidAnniversaryEventEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAnniversaryEventEntryId
api_type:
- COM
ms.assetid: 177b2b87-7a06-4d53-8f03-5bec5632c2dd
description: "Last modified: March 09, 2015"
---

# PidLidAnniversaryEventEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the entry identifier of the appointment that represents the contact's anniversary.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidAnniversaryEventEID  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x0000804E  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

The appointment specified by the **dispidAnniversaryEventEID** property must be linked to this contact by using the **dispidContactLinkEntry** ( [PidLidContactLinkEntry](pidlidcontactlinkentry-canonical-property.md)), **dispidContactLinkSearchKey** ( [PidLidContactLinkSearchKey](pidlidcontactlinksearchkey-canonical-property.md)), and **dispidContactLinkName** ( [PidLidContactLinkName](pidlidcontactlinkname-canonical-property.md)) properties, as detailed in [[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx).
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
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

