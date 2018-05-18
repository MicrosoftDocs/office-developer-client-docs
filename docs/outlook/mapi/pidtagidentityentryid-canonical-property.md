---
title: "PidTagIdentityEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagIdentityEntryId
api_type:
- HeaderDef
ms.assetid: 61a9d403-e0e5-45c3-8d18-4d53207ab927
description: "Last modified: March 09, 2015"
---

# PidTagIdentityEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the entry identifier for a service provider's identity as defined within a messaging system. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_IDENTITY_ENTRYID  <br/> |
|Identifier:  <br/> |0x3E01  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

This property does not appear as a property on any object but only as a column in a status table. It is part of the identity of the service provider exposing the status table row. The provider's identity typically refers to its account on the server, but can refer to any representation the provider defines within the messaging system. 
  
This proprerty is commonly set to the appropriate address book entry identifier. 
  
A service provider furnishing any of the identity properties should furnish all of them. Providers that belong to the same message service should expose the same values for the identity properties. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[IMAPISession::QueryIdentity](imapisession-queryidentity.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

