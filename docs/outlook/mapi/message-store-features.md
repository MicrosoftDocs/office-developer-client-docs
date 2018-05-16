---
title: "Message Store Features"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d9167cd2-fc88-46b1-9a26-151955fb606c
description: "Last modified: March 09, 2015"
 
 
---

# Message Store Features

  
  
**Applies to**: Outlook 
  
Message store providers are more complex than other MAPI service providers in that message store providers have a wider range of optional features they can implement. The list of required features for a message store provider is fairly short. However, a typical message store provider will support a number of optional features, because many of the optional features are very useful or required by most MAPI clients. The following table lists the major features that message store providers can implement and whether each feature is required or optional for all message store providers and for default message store providers.
  
|**Feature**|**All**|**Default**|
|:-----|:-----|:-----|
|Providing status with the MAPI status table.  <br/> |Required  <br/> |Required  <br/> |
|Implementing folder objects.  <br/> |Required  <br/> |Required  <br/> |
|Implementing message objects.  <br/> |Required  <br/> |Required  <br/> |
|Providing read and nonread reports.  <br/> |Required  <br/> |Required  <br/> |
|Providing a progress interface.  <br/> |Required  <br/> |Required  <br/> |
|Providing a configuration interface.  <br/> |Required  <br/> |Required  <br/> |
|Supporting associated contents tables for form and view support.  <br/> |Optional  <br/> |Optional  <br/> |
|Sending messages with the message store provider.  <br/> |Optional  <br/> |Required  <br/> |
|Receiving messages with the message store provider.  <br/> |Optional  <br/> |Required  <br/> |
|Supporting message attachments.  <br/> |Optional  <br/> |Optional  <br/> |
|Supporting Rich Text Format for messages.  <br/> |Optional  <br/> |Optional  <br/> |
|Providing notifications.  <br/> |Optional  <br/> |Optional  <br/> |
|Supporting searches.  <br/> |Optional  <br/> |Optional  <br/> |
|Supporting tightly coupled message store/transport providers.  <br/> |Optional  <br/> |Optional  <br/> |
|Supporting non-reuse of entry identifiers.  <br/> |Optional  <br/> |Optional  <br/> |
   
Many of the optional features can be advertised to MAPI and client applications by setting various flags in the message store object's **PR_STORE_SUPPORT_MASK** ( [PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property. The required features do not have flags associated with them. **PR_STORE_SUPPORT_MASK** is required on message store, folder, and message objects. 
  
## See also

#### Concepts

[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

