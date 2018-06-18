---
title: "PidTagDefCreateDl Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagDefCreateDl
api_type:
- HeaderDef
ms.assetid: 172dc15b-7bda-403f-a93a-446b2f9ff1d3
description: "Last modified: March 09, 2015"
---

# PidTagDefCreateDl Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the template entry identifier for a default distribution list. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DEF_CREATE_DL  <br/> |
|Identifier:  <br/> |0x3611  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

Client applications use this property to create a distribution list within a container. Support of entry creation is optional for address book containers; those that do not support it are not required to expose this property. 
  
This property specifies an entry that can appear in the **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property for distribution lists. After obtaining the identifier, the client uses it in a call to the [IABContainer::CreateEntry](iabcontainer-createentry.md) method. The entry represents the template for the default distribution list. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[IABLogon::CompareEntryIDs](iablogon-compareentryids.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

