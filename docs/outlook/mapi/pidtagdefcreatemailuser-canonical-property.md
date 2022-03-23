---
title: "PidTagDefCreateMailuser Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDefCreateMailuser
api_type:
- HeaderDef
ms.assetid: e8293dc9-f2f1-4065-89f4-e734a8db63df
description: "Contains the template entry identifier for a default messaging user object. Client applications use this property to create a messaging user object within a container."
---

# PidTagDefCreateMailuser Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the template entry identifier for a default messaging user object. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_DEF_CREATE_MAILUSER  <br/> |
|Identifier:  <br/> |0x3612  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Address book  <br/> |
   
## Remarks

Client applications use this property to create a messaging user object within a container. Support of entry creation is optional for address book containers; those that do not support it are not required to expose this property. 
  
This property specifies an entry that can appear in the **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property for messaging users. After obtaining the identifier, the client uses it in a call to the [IABContainer::CreateEntry](iabcontainer-createentry.md) method. The entry represents the template for the default messaging user. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

