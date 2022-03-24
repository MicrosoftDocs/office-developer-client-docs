---
title: "PidTagRecordKey Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRecordKey
api_type:
- COM
ms.assetid: a12fb9a2-799d-4112-b26c-4b2854c47cc2
description: "Contains a unique binary-comparable identifier for a specific object. This property cannot be used to open an object."
---

# PidTagRecordKey Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a unique binary-comparable identifier for a specific object.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RECORD_KEY  <br/> |
|Identifier:  <br/> |0x0FF9  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |ID properties  <br/> |
   
## Remarks

This property facilitates locating references to an object, such as finding its row in a contents table. This property cannot be used to open an object; use the entry identifier for that purpose.
  
An attachment subobject should be uniquely identified within a message by this property. This identifier is the only attachment characteristic guaranteed to stay the same after the message is closed and reopened. The store provider must preserve this property across sessions to ensure this guarantee.
  
For folders, this property contains a key used in the folder hierarchy table. Typically this is the same value as that provided by the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
  
For message stores, this property is identical to the **PR_STORE_RECORD_KEY** ([PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md)) property.
  
In a message store object, this property should be unique across all store providers. One way to do this is to combine the value of the **PR_MDB_PROVIDER** ([PidTagStoreProvider](pidtagstoreprovider-canonical-property.md)) property for the store (unique to that provider type) with a [GUID](guid.md) structure or other value unique to the specific message store. 
  
This property is always available through the [IMAPIProp::GetProps](imapiprop-getprops.md) method following the first call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. Some providers can make it available immediately after instantiation. 
  
A client or service provider can compare values from this property by using memcmp. This is not possible for entry identifier values. However, this property is guaranteed to be unique within the same message store or address book container; two objects from different containers can have the same value of this property.
  
One distinction between the record and search keys is that the record key is specific to the object, whereas the search key can be copied to other objects. For example, two copies of the object can have the same **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) value but must have different values for this property.
  
The following table summarizes important differences among **PR_ENTRYID**, **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) and this property. 
  
|**Characteristic**|**PR_ENTRYID**|**PR_RECORD_KEY**|**PR_SEARCH_KEY**|
|:-----|:-----|:-----|:-----|
|Required on attachment objects  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Required on folder objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on message store objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on status objects  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|Creatable by client  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Available before a call to **SaveChanges** <br/> |Maybe  <br/> |Maybe  <br/> |Messages Yes Others Maybe  <br/> |
|Changed in a copy operation  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Changeable by a client after a copy  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Unique within ... |Entire world  <br/> |Provider instance  <br/> |Entire world  <br/> |
|Binary comparable (as with memcmp)  <br/> |No -- use **IMAPISupport:: CompareEntryIDs** <br/> |Yes  <br/> |Yes  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

