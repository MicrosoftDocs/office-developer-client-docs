---
title: "PidTagEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagEntryId
api_type:
- HeaderDef
ms.assetid: ca02e873-c2d2-4d58-8df8-c05fbcdc8fba
description: "Last modified: March 09, 2015"
---

# PidTagEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a MAPI entry identifier used to open and edit properties of a particular MAPI object. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ENTRYID  <br/> |
|Identifier:  <br/> |0x0FFF  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |ID properties  <br/> |
   
## Remarks

This property identifies an object for **OpenEntry** to instantiate and provides access to all of its properties through the appropriate derived interface of **IMAPIProp**. 
  
This property is one of the base address properties for all messaging users. 
  
This property can contain either a long-term or a short-term identifier. Short-term identifiers are easier and faster to construct, but are limited in their scope and duration, typically to the current session and workstation. They are commonly used for objects of a temporary nature, such as table rows or dialog box entries, and then abandoned. Long-term identifiers are used for objects of a more wide-ranging and long-lasting nature. 
  
This property is always available through the [IMAPIProp::GetProps](imapiprop-getprops.md) method following the first call to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. Some service providers can make it available immediately after instantiation. The provider must always return a long-term entry identifier from **GetProps**. Therefore, to convert a short-term identifier to long-term, simply open the object and get its this property through **GetProps**. 
  
The following table summarizes important differences among this property, **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)), and **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)). 
  
|**Characteristic**|**PR_ENTRYID**|**PR_RECORD_KEY**|**PR_SEARCH_KEY**|
|:-----|:-----|:-----|:-----|
|Required on attachment objects  <br/> |No  <br/> |Yes  <br/> |No  <br/> |
|Required on folder objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on message store objects  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Required on status objects  <br/> |Yes  <br/> |No  <br/> |No  <br/> |
|Created by client  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Available before call to **SaveChanges** <br/> |Depends on provider implementation  <br/> |Depends on provider implementation  <br/> |For messages, Yes. For others, depends on provider implementation.  <br/> |
|Changed in a copy operation  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Changeable by client after a copy  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Unique within  <br/> |Entire world  <br/> |Provider instance  <br/> |Entire world  <br/> |
|Binary comparable (as with memcmp)  <br/> |No use [IMAPISupport:: CompareEntryIDs](imapisupport-compareentryids.md) <br/> |Yes  <br/> |Yes  <br/> |
   
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles the order and flow for data transfers between a client and server.
    
[[MS-OXCPERM]](http://msdn.microsoft.com/library/944ddb65-6249-4c34-a46e-363fcd37195e%28Office.15%29.aspx)
  
> Handles the retrieval of folder permission lists that are stored on the server.
    
[[MS-OXODLGT]](http://msdn.microsoft.com/library/01a89b11-9c43-4c40-b147-8f6a1ef5a44f%28Office.15%29.aspx)
  
> Specifies methods for connecting to and configuring mailboxes as delegates, and interactions with message and calendar objects when they act on behalf of another user.
    
[[MS-OXWAVLS]](http://msdn.microsoft.com/library/69a276d8-5fc3-40ba-acd0-31cf42e6af58%28Office.15%29.aspx)
  
> Specifies the schema and methods that are used to request availability information for users and resources.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagStoreEntryId Canonical Property](pidtagstoreentryid-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

