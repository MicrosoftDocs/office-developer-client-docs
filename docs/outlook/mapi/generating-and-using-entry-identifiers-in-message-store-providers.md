---
title: "Generating and using entry identifiers in message store providers"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 0c43546a-4788-4852-bc89-d6baa4f33c94
---

# Generating and using entry identifiers in message store providers

**Applies to**: Outlook 2013 | Outlook 2016 
  
When a new folder or message is created in a message store, the message store provider has to assign that object an entry identifier so that client applications can refer to it. Message store providers can either reuse the defunct long-term entry identifiers of deleted objects or create new identifiers. There is no requirement one way or the other for message store providers; however, if it is feasible, a message store provider should always generate new long-term entry identifiers for new objects rather than reusing old ones. It is fine to reuse short-term entry identifiers when the objects they refer to are deleted.
  
The reason for this deletion is that clients can cache entry identifiers, sometimes for long periods of time. If that happens and the message store provider does reuse entry identifiers, it is possible for the entry identifier to refer to a different object when the client opens the entry identifier than when it first obtained the entry identifier. If the message store provider does not reuse entry identifiers — or at least uses an entry identifier generation scheme that does not repeat for a very long time — this problem cannot occur.
  
Similarly, message store providers should attempt to preserve entry identifiers for folders and messages when they are moved in the message store. If the message store provider can do that, references to objects in the store will not become invalid when the object is moved to a different location in the store.
  
## See also

- [Message Store Features](message-store-features.md)

