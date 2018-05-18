---
title: "Contents Tables"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7b8efb4e-b5be-41b8-81bb-9aa1da421433
description: "Last modified: March 09, 2015"
 
 
---

# Contents Tables

  
  
**Applies to**: Outlook 
  
A contents table contains information about objects in a MAPI container. Address book providers implement contents tables for each of their containers, and message store and remote transport providers implement contents tables for their folders. The contents table of an address book container lists information about its messaging user and distribution list objects, while the contents table of a folder lists information about its messages. Contents tables are used primarily by client applications. 
  
There are two types of folder contents tables:
  
- Standard contents tables contain standard messages — messages that can be transmitted and made visible to a user. 
    
- Associated contents tables contain hidden, non-transmittable information created by a client for a specific purpose, such as to store an alternate representation of a standard message. Associated information is created by passing the MAPI_ASSOCIATED flag to the [IMAPIFolder::CreateMessage](imapifolder-createmessage.md) call. 
    
The contents tables of most address book containers and many folders do not support categorized sorting. 
  
A contents table can be accessed by calling:
  
- [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md).
    
    - Or -
    
- [IMAPIProp::OpenProperty](imapiprop-openproperty.md) with **PR_CONTAINER_CONTENTS** ([PidTagContainerContents](pidtagcontainercontents-canonical-property.md)) or **PR_FOLDER_ASSOCIATED_CONTENTS** ([PidTagFolderAssociatedContents](pidtagfolderassociatedcontents-canonical-property.md)) (folders only) specified as the property tag and IID_IMAPITable as the interface identifier.
    
Message store and address book providers must support both techniques for retrieving table properties. It is unacceptable for providers to support only one way for accessing these tables because clients expect to have the choice. 
  
 **GetContentsTable** accepts as input several flags that specify preferences. When set, the MAPI_ASSOCIATED flag retrieves an associated contents table. Because some folders do not support associated contents, and there is no way for clients to determine this ahead of time, **GetContentsTable** sometimes returns the error MAPI_E_NO_SUPPORT when an associated contents table is requested. 
  
The MAPI_DEFERRED_ERRORS flag indicates to the implementer of the table that any errors encountered during the call do not need to be reported until some later time. 
  
The call to **IMAPIProp::OpenProperty** involves accessing a contents table by opening its corresponding property, **PR_CONTAINER_CONTENTS** for address book contents tables and standard folder contents tables, and **PR_FOLDER_ASSOCIATED_CONTENTS** for associated contents tables. Although neither or these properties can be retrieved through a folder or container's [IMAPIProp::GetProps](imapiprop-getprops.md) method, they are included in the property tag array that is returned by the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method. 
  
 **PR_CONTAINER_CONTENTS** can also be used to include or exclude a contents table from a copy operation. If a client specifies **PR_CONTAINER_CONTENTS** in the  *lpExcludeProps*  parameter for **IMAPIProp::CopyTo** in a copy operation, the new folder or container will not support the contents table of the original folder or container. 
  
Address book container and folder contents tables have a lengthy list of required columns — columns that clients can expect to be available after they retrieve the table from **GetContentsTable** or **OpenProperty**. Providers can add to this required set if necessary and clients, through the **SetColumns** method, can also request modifications. 
  
The required columns for each of the types of contents tables are:
  
|**Required column**|**Type of contents table**|
|:-----|:-----|
|**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_DISPLAY_CC** ([PidTagDisplayCc](pidtagdisplaycc-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_DISPLAY_TO** ([PidTagDisplayTo](pidtagdisplayto-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |All contents tables  <br/> |
|**PR_HASATTACH** ([PidTagHasAttachments](pidtaghasattachments-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))  <br/> |All contents tables  <br/> |
|**PR_LAST_MODIFICATION_TIME** ([PidTagLastModificationTime](pidtaglastmodificationtime-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_MAPPING_SIGNATURE** ([PidTagMappingSignature](pidtagmappingsignature-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_MESSAGE_DOWNLOAD_TIME** ([PidTagMessageDownloadTime](pidtagmessagedownloadtime-canonical-property.md))  <br/> |Remote transport folder tables  <br/> |
|**PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_MESSAGE_SIZE** ([PidTagMessageSize](pidtagmessagesize-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_MSG_STATUS** ([PidTagMessageStatus](pidtagmessagestatus-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |All contents tables  <br/> |
|**PR_PARENT_ENTRYID** ([PidTagParentEntryId](pidtagparententryid-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md))  <br/> |Address book container and message store folder tables  <br/> |
|**PR_SENT_REPRESENTING_NAME** ([PidTagSentRepresentingName](pidtagsentrepresentingname-canonical-property.md))  <br/> |Remote transport folder tables  <br/> |
|**PR_STORE_ENTRYID** ([PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_STORE_RECORD_KEY** ([PidTagStoreRecordKey](pidtagstorerecordkey-canonical-property.md))  <br/> |Message store folder tables  <br/> |
   
The entry identifier available with each row can either be a short- or long-term entry identifier, depending on the table implementation. Short-term entry identifiers are typically used in situations where performance is an issue. Either type of entry identifier can be used to access the corresponding object. 
  
Contents tables also have a set of columns that are optional but commonly included by service providers in their implementations. These optional columns are:
  
|**Optional column**|**Type of contents table**|
|:-----|:-----|
|**PR_CLIENT_SUBMIT_TIME** ([PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))  <br/> |Standard folder contents tables  <br/> |
|**PR_CONTENT_UNREAD** ([PidTagContentUnreadCount](pidtagcontentunreadcount-canonical-property.md))  <br/> |Standard folder contents tables  <br/> |
|**PR_CONVERSATION_INDEX** ([PidTagConversationIndex](pidtagconversationindex-canonical-property.md))  <br/> |Message store folder tables  <br/> |
|**PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_IMPORTANCE** ([PidTagImportance](pidtagimportance-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_MESSAGE_DELIVERY_TIME** ([PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_NORMALIZED_SUBJECT** ([PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_PRIORITY** ([PidTagPriority](pidtagpriority-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md))  <br/> |Address book container tables  <br/> |
|**PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_SENSITIVITY** ([PidTagSensitivity](pidtagsensitivity-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md))  <br/> |All folder contents tables  <br/> |
|**PR_TRANSMITABLE_DISPLAY_NAME** ([PidTagTransmittableDisplayName](pidtagtransmittabledisplayname-canonical-property.md))  <br/> |Address book container tables  <br/> |
   
Message store providers must also include **PR_PARENT_DISPLAY** ([PidTagParentDisplay](pidtagparentdisplay-canonical-property.md)) for search-result folders contents tables only.
  
Named properties may be added to the column set of a folder contents table only if all messages in the folder have the same mapping signature, that is, the same mapping of property names to property identifiers. Folder contents tables should support adding message class specific properties to the column set, if they support the creation of arbitrary messages in the folder.
  
Clients can save the default sort order for a folder contents table by calling its [IMAPIFolder::SaveContentsSort](imapifolder-savecontentssort.md) method. If the RECURSIVE_SORT flag is specified on the call, the sort order can be made to apply to all of the subfolders within the folder. 
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

