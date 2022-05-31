---
title: "Message Store Features"
description: "Describes the major features that message store providers can implement and whether each feature is required or optional for certain store providers."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: d9167cd2-fc88-46b1-9a26-151955fb606c
 
 
---

# Message Store Features

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Message store providers are more complex than other MAPI service providers in that message store providers have a wider range of optional features they can implement. The list of required features for a message store provider is fairly short. However, a typical message store provider will support a number of optional features, because many of the optional features are very useful or required by most MAPI clients. The following table lists the major features that message store providers can implement and whether each feature is required or optional for all message store providers and for default message store providers.
  
|**Feature**|**All**|**Default**|
|:-----|:-----|:-----|
|Providing status with the MAPI status table. |Required  <br/> |Required  <br/> |
|Implementing folder objects. |Required  <br/> |Required  <br/> |
|Implementing message objects. |Required  <br/> |Required  <br/> |
|Providing read and nonread reports. |Required  <br/> |Required  <br/> |
|Providing a progress interface. |Required  <br/> |Required  <br/> |
|Providing a configuration interface. |Required  <br/> |Required  <br/> |
|Supporting associated contents tables for form and view support. |Optional  <br/> |Optional  <br/> |
|Sending messages with the message store provider. |Optional  <br/> |Required  <br/> |
|Receiving messages with the message store provider. |Optional  <br/> |Required  <br/> |
|Supporting message attachments. |Optional  <br/> |Optional  <br/> |
|Supporting Rich Text Format for messages. |Optional  <br/> |Optional  <br/> |
|Providing notifications. |Optional  <br/> |Optional  <br/> |
|Supporting searches. |Optional  <br/> |Optional  <br/> |
|Supporting tightly coupled message store/transport providers. |Optional  <br/> |Optional  <br/> |
|Supporting non-reuse of entry identifiers. |Optional  <br/> |Optional  <br/> |
   
Many of the optional features can be advertised to MAPI and client applications by setting various flags in the message store object's **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property. The required features do not have flags associated with them. **PR_STORE_SUPPORT_MASK** is required on message store, folder, and message objects. 
  
## See also



[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

