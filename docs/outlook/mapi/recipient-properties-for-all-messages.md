---
title: "Recipient Properties for All Messages"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 18c96796-f38d-4058-9c51-9c5a14990846
description: "Last modified: March 09, 2015"
 
 
---

# Recipient Properties for All Messages

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The following properties are typically present for all message recipients. **PR_EMAIL_ADDRESS** and **PR_SEARCH_KEY** are optional; all of the other properties are required. 
  
**Table Title**

|**Property**|**Description**|
|:-----|:-----|
|**PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))  <br/> |Contains the messaging user's email address type, such as SMTP. |
|**PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))  <br/> |Contains the display name for a given MAPI object. |
|**PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))  <br/> |Contains a value used to associate an icon with a particular row of a table. |
|**PR_EMAIL_ADDRESS** ([PidTagEmailAddress](pidtagemailaddress-canonical-property.md))  <br/> |Contains the messaging user's email address. |
|**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))  <br/> |Contains a MAPI entry identifier used to open and edit properties of a particular MAPI object. |
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Contains the type of an object. |
|**PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md))  <br/> |Contains a binary-comparable key that identifies correlated objects for a search. |
   

