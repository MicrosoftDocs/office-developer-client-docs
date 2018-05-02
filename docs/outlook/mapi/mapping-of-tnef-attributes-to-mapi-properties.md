---
title: "Mapping of TNEF Attributes to MAPI Properties"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 1a724fac-2e64-48a7-92b5-d7cf1528cb2c
description: "Last modified: March 09, 2015"
 
 
---

# Mapping of TNEF Attributes to MAPI Properties

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
The following table lists all the attributes defined in the TNEF implementation and their mappings to MAPI properties. In some cases, multiple MAPI properties are encoded as a single attribute. Some attributes have extended descriptions later in this section.
  
|**TNEF attribute**|**MAPI property or properties**|
|:-----|:-----|
|**attAidOwner** <br/> |**PR_OWNER_APPT_ID** ( [PidTagOwnerAppointmentId](pidtagownerappointmentid-canonical-property.md))  <br/> |
|**attAttachCreateDate** <br/> |**PR_CREATION_TIME** ( [PidTagCreationTime](pidtagcreationtime-canonical-property.md))  <br/> |
|**attAttachData** <br/> |**PR_ATTACH_DATA_BIN** ( [PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) or **PR_ATTACH_DATA_OBJ** ( [PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md))  <br/> |
|**attAttachment** <br/> |For information about this mapping, see [TNEF Attributes](tnef-attributes.md).  <br/> |
|**attAttachMetaFile** <br/> |**PR_ATTACH_RENDERING** ( [PidTagAttachRendering](pidtagattachrendering-canonical-property.md))  <br/> |
|**attAttachModifyDate** <br/> |**PR_LAST_MODIFICATION_TIME** ( [PidTagLastModificationTime](pidtaglastmodificationtime-canonical-property.md))  <br/> |
|**attAttachRenddata** <br/> |**PR_ATTACH_METHOD** ( [PidTagAttachMethod](pidtagattachmethod-canonical-property.md)), **PR_RENDERING_POSITION** ( [PidTagRenderingPosition](pidtagrenderingposition-canonical-property.md))  <br/> |
|**attAttachTitle** <br/> |**PR_ATTACH_FILENAME** ( [PidTagAttachFilename](pidtagattachfilename-canonical-property.md))  <br/> |
|**attAttachTransportFilename** <br/> |**PR_ATTACH_TRANSPORT_NAME** ( [PidTagAttachTransportName](pidtagattachtransportname-canonical-property.md))  <br/> |
|**attBody** <br/> |**PR_BODY** ( [PidTagBody](pidtagbody-canonical-property.md))  <br/> |
|**attConversationID** <br/> |**PR_CONVERSATION_KEY** ( [PidTagConversationKey](pidtagconversationkey-canonical-property.md)) This property has been deprecated in Microsoft Exchange Server: Its use persists in Outlook only, for locating **IPM.MessageManager** messages.  <br/> |
|**attDateEnd** <br/> |**PR_END_DATE** ( [PidTagEndDate](pidtagenddate-canonical-property.md)) See [attDate Attributes](attdate-attributes.md) for details.  <br/> |
|**attDateModified** <br/> |**PR_LAST_MODIFICATION_TIME** See [attDate Attributes](attdate-attributes.md) for details.  <br/> |
|**attDateRecd** <br/> |**PR_MESSAGE_DELIVERY_TIME** ( [PidTagMessageDeliveryTime](pidtagmessagedeliverytime-canonical-property.md)) See [attDate Attributes](attdate-attributes.md) for details.  <br/> |
|**attDateSent** <br/> |**PR_CLIENT_SUBMIT_TIME** ( [PidTagClientSubmitTime](pidtagclientsubmittime-canonical-property.md)) See [attDate Attributes](attdate-attributes.md) for details.  <br/> |
|**attDateStart** <br/> |**PR_START_DATE** ( [PidTagStartDate](pidtagstartdate-canonical-property.md)) See [attDate Attributes](attdate-attributes.md) for details.  <br/> |
|**attFrom** <br/> |**PR_SENDER_ENTRYID** ( [PidTagSenderEntryId](pidtagsenderentryid-canonical-property.md)) and **PR_SENDER_NAME** ( [PidTagSenderName](pidtagsendername-canonical-property.md))  <br/> |
|**attMAPIProps** <br/> |For information about this attribute, see [attMAPIProps](attmapiprops.md).  <br/> |
|**attMessageClass** <br/> |**PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md))  <br/> |
|**attMessageID** <br/> |**PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) See [TNEF Correlation in X.400 Gateways and Transports](tnef-correlation-in-x-400-gateways-and-transports.md).  <br/> |
|**attMessageStatus** <br/> |**PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md))  <br/> |
|**attOriginalMessageClass** <br/> |**PR_ORIG_MESSAGE_CLASS ** ( [PidTagOriginalMessageClass](pidtagoriginalmessageclass-canonical-property.md))  <br/> |
|**attOwner** <br/> |See [attOwner](attowner.md).  <br/> |
|**attParentID** <br/> |**PR_PARENT_KEY** ( **PidTagParentKey**) This property has been deprecated. See [API Elements Deprecated in This Edition](api-elements-deprecated-in-this-edition.md) for more information.  <br/> |
|**attPriority** <br/> |**PR_PRIORITY** ( [PidTagPriority](pidtagpriority-canonical-property.md))  <br/> |
|**attRecipTable** <br/> |**PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md))  <br/> |
|**attRequestRes** <br/> |**PR_RESPONSE_REQUESTED** ( [PidTagResponseRequested](pidtagresponserequested-canonical-property.md))  <br/> |
|**attSentFor** <br/> |**PR_SENT_REPRESENTING_ENTRYID** ( [PidTagSentRepresentingEntryId](pidtagsentrepresentingentryid-canonical-property.md))  <br/> |
|**attSubject** <br/> |**PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md))  <br/> |
   

