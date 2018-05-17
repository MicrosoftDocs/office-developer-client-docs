---
title: "PidTagCreateTemplates Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagCreateTemplates
api_type:
- HeaderDef
ms.assetid: d2530009-5de3-4872-a0a5-be1389c4206e
description: "Last modified: March 09, 2015"
---

# PidTagCreateTemplates Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an embedded table object that contains dialog box template entry identifiers. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CREATE_TEMPLATES  <br/> |
|Identifier:  <br/> |0x3604  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

To learn what template objects can be created inside a container, call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method on this property. The resulting object is the one-off table that gives the entry identifiers for all the templates that you can create inside the container. 
  
To create the template objects, call the container object's **CreateEntry** method on the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) column values from the one-off table.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Reference

[IABContainer::CreateEntry](iabcontainer-createentry.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

