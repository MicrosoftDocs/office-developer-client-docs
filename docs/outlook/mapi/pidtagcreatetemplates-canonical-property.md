---
title: "PidTagCreateTemplates Canonical Property"
description: Outlines the PidTagCreateTemplates canonical property, which contains an embedded table object that contains dialog box template entry identifiers.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagCreateTemplates
api_type:
- HeaderDef
ms.assetid: d2530009-5de3-4872-a0a5-be1389c4206e
---

# PidTagCreateTemplates Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an embedded table object that contains dialog box template entry identifiers. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CREATE_TEMPLATES  <br/> |
|Identifier:  <br/> |0x3604  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

To learn what template objects can be created inside a container, call the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method on this property. The resulting object is the one-off table that gives the entry identifiers for all the templates that you can create inside the container. 
  
To create the template objects, call the container object's **CreateEntry** method on the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) column values from the one-off table.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[IABContainer::CreateEntry](iabcontainer-createentry.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

