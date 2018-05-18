---
title: "IABContainer  IMAPIContainer"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABContainer
api_type:
- COM
ms.assetid: 1f5ce6e0-b79a-4da2-b014-8c00cd72912e
description: "Last modified: March 09, 2015"
---

# IABContainer : IMAPIContainer

  
  
**Applies to**: Outlook 
  
Provides access to address book containers. MAPI and client applications call the methods of **IABContainer** to perform name resolution and to create, copy, and delete recipients. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Address book container objects  <br/> |
|Implemented by:  <br/> |Address book providers  <br/> |
|Called by:  <br/> |MAPI and client applications  <br/> |
|Interface identifier:  <br/> |IID_IABContainer  <br/> |
|Pointer type:  <br/> |LPABCONT  <br/> |
|Transaction model:  <br/> |Transacted  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[CreateEntry](iabcontainer-createentry.md) <br/> |Creates a new entry, which can be a messaging user, a distribution list, or another container.  <br/> |
|[CopyEntries](iabcontainer-copyentries.md) <br/> |Copies one or more entries, typically messaging users or distribution lists.  <br/> |
|[DeleteEntries](iabcontainer-deleteentries.md) <br/> |Removes one or more entries, typically messaging users, distribution lists, or other containers.  <br/> |
|[ResolveNames](iabcontainer-resolvenames.md) <br/> |Performs name resolution for one or more recipient entries.  <br/> |
   
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Read/write  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Read-only  <br/> |
   
|**Optional properties**|**Access**|
|:-----|:-----|
|**PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DEF_CREATE_DL** ([PidTagDefCreateDl](pidtagdefcreatedl-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DEF_CREATE_MAILUSER** ([PidTagDefCreateMailuser](pidtagdefcreatemailuser-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |Read-only  <br/> |
   
## Remarks

The **IABContainer** interface inherits indirectly from the [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28VS.85%29.aspx) interface through the [IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md) and [IMAPIProp : IUnknown](imapipropiunknown.md) interfaces. Address book providers implement the **IABContainer** interface. 
  
Any number of messaging user objects, distribution lists, and other address book containers can exist in an address book container. As with any container, clients or service providers can use an address book container to open one of its entries or to retrieve a hierarchy table or contents table. Address book containers also provide name resolution and, depending on the provider, the ability to add, remove, or modify entries.
  
MAPI defines a special address book container called the personal address book (PAB) that holds entries copied from other containers. A PAB is always modifiable. Users typically populate their PAB with entries designating the recipients with which they most frequently communicate. A PAB can also hold one-off addresses and new recipients not yet a part of any address book container.
  
## See also

#### Concepts

[MAPI Interfaces](mapi-interfaces.md)

