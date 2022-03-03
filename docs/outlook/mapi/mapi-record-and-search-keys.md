---
title: "MAPI Record and Search Keys"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: caa7b7f3-a5a1-4f07-98c9-22652ecd5d21
 
 
---

# MAPI Record and Search Keys

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Record keys and search keys are binary identifiers that are assigned to many MAPI objects. Unlike an object's entry identifier, its record or search key is directly comparable as well as transmittable. 
  
## Record Keys

A record key is used to compare two objects. Message store and address book objects must have record keys, which are stored in their **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)) property. Because a record key identifies an object and not its data, every instance of an object has a unique record key. The scope of a record key for folders and messages is the message store. The scope for address book containers, messaging users, and distribution lists is the set of top-level containers provided by MAPI for use in the integrated address book.
  
Record keys can be duplicated in another resource. For example, different messages in two different message stores can have the same record key. This is different from long-term entry identifiers; because long-term entry identifiers contain a reference to the service provider, they have a wider scope. A message store's record key is similar in scope to a long-term entry identifier; it should be unique across all message store providers. To ensure this uniqueness, message store providers typically set their record key to a value that is the combination of their **PR_MDB_PROVIDER** ([PidTagStoreProvider](pidtagstoreprovider-canonical-property.md)) property and an identifier that is unique to the message store.
  
## Search Keys

A search key is used to compare the data in two objects. An object's search key is stored in its **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) property. Because a search key represents an object's data and not the object itself, two different objects with the same data can have the same search key. When an object is copied, for example, both the original object and its copy have the same data and the same search key.
  
Messages and messaging users have search keys. The search key of a message is a unique identifier of the message's data. Message store providers furnish a message's **PR_SEARCH_KEY** property at message creation time. The search key of an address book entry is computed from its address type (**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))) and address (**PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))). If the address book entry is writeable, its search key might not be available until the address type and address have been set by using the [IMAPIProp::SetProps](imapiprop-setprops.md) method and the entry has been saved by using the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method. When these address properties change, it is possible for the corresponding search key not to be synchronized with the new values until the changes have been committed with a **SaveChanges** call. 
  
The value of an object's record key can be the same as or different than the value of its search key, depending on the service provider. Some service providers use the same value for an object's search key, record key, and entry identifier. Other service providers assign unique values for each of its objects' identifiers. 
  
## See also



[MAPI Application Development](mapi-application-development.md)

