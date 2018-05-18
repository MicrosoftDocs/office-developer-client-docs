---
title: "Mappings and Mapping Signatures"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 773f6671-cc21-4d1f-a11d-308bc71c852d
description: "Last modified: July 23, 2011"
 
 
---

# Mappings and Mapping Signatures

  
  
**Applies to**: Outlook 
  
When a service provider supports named properties, each set of identifier and name pairs is referred to as a mapping. Service providers can support one mapping or several. That is, one message store provider, for example, can implement the **GetIDsFromNames** and **GetNamesFromIDs** methods for all of its message, folder, and message store objects to work with a single list of names and their corresponding identifiers. Another message store provider might have one list for every folder and the messages contained within it, or implement a unique list for every message and every folder. Message store providers that use a unique mapping for every message must not allow named properties to appear in their folder contents tables because for a given property name, the property identifier will differ from message to message. MAPI recommends that providers keep it simple and operate with a single list for all of their objects including tables. 
  
For every mapping, service providers must supply a mapping signature. A mapping signature is a binary value, usually a GUID, that uniquely identifies a set of property identifiers and their corresponding names. Mapping signatures are stored in an object's **PR_MAPPING_SIGNATURE** ([PidTagMappingSignature](pidtagmappingsignature-canonical-property.md)) property. Service providers must change the value for their **PR_MAPPING_SIGNATURE** property whenever a change is made to the mapping that it represents. For example, **PR_MAPPING_SIGNATURE** must be updated if a new identifier is assigned to a name or a new name and identifier pair is added. 
  
Clients working with the named properties of objects use the objects' **PR_MAPPING_SIGNATURE** properties in comparison and copy operations. To compare named property identifiers belonging to two objects, clients not using mapping signatures must call [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) on both objects to retrieve the names for each of the identifiers. Using the mapping signatures of objects can render this call unnecessary. When two objects have the same value for their **PR_MAPPING_SIGNATURE** properties, they use the same mapping. Identifiers that use the same mapping can be compared directly. Service providers that implement [IMAPIProp::CopyTo](imapiprop-copyto.md) and [IMAPIProp::CopyProps](imapiprop-copyprops.md) can also take advantage of an object's mapping signature. When copying named properties between objects, service providers can avoid the conversion step when the source and destination objects have the same mapping signature. 
  
## See also

#### Reference

[IMAPIProp : IUnknown](imapipropiunknown.md)
#### Concepts

[MAPI Named Properties](mapi-named-properties.md)

