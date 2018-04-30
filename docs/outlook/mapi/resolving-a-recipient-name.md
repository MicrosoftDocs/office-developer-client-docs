---
title: "Resolving a Recipient Name"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 2baed391-85bd-4e88-8800-c19bc2d2d54a
description: "Last modified: July 23, 2011"
---

# Resolving a Recipient Name

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
When a message is addressed, a recipient list is built with properties relating to each recipient. By the time the message is sent, one of those properties must be the recipient's long-term entry identifier. To ensure that each recipient includes the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property, pass the [ADRLIST](adrlist.md) structure describing your recipient list in the contents of the  _lpAdrList_ parameter in a call to [IAddrBook::ResolveName](iaddrbook-resolvename.md).
  
 **ResolveName** begins processing by ignoring the entries in the **ADRLIST** structure that have already been resolved, as indicated by the presence of an entry identifier in the corresponding [ADRENTRY](adrentry.md) structure's **SPropValue** array. Next, **ResolveName** automatically assigns one-off entry identifiers to two types of recipients: 
  
- Recipients with an address formatted as an Internet address
    
- Recipients with an address formatted as follows:
    
     `displayname[address type:e-mail address]`
    
For all remaining entries, **ResolveName** searches the address book for an exact match on the display name. **ResolveName** uses the **PR_AB_SEARCH_PATH** ( [PidTagAbSearchPath](pidtagabsearchpath-canonical-property.md)) property to determine the set of containers to search and the search order. MAPI calls the [IABContainer::ResolveNames](iabcontainer-resolvenames.md) method of every container to attempt to resolve all of the names. Because some containers do not support **ResolveNames**, if the container returns MAPI_E_NO_SUPPORT, MAPI applies a **PR_ANR** ( [PidTagAnr](pidtaganr-canonical-property.md)) property restriction against its contents table. All address book containers are required to support name resolution with this restriction. Once all the names are resolved, no further container calls are made. If all the containers have been called, but ambiguous or unresolved names remain, MAPI displays a dialog box if possible to prompt the user to resolve the remaining names.
  
The **PR_ANR** restriction matches the value of the **PR_ANR** property against the display name in the **ADRLIST** structure. Limiting the view of a container's contents table with the **PR_ANR** property restriction causes the address book provider to perform a "best guess" type of search, matching against the property that makes sense for the provider. For example, one address book provider might always match names in the recipient list against **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) while another might allow an administrator to select the property.
  
 **To set a PR_ANR property restriction on an address book container's contents table**
  
1. Create an [SRestriction](srestriction.md) structure as shown in the following code: 
    
  ```
  SRestriction SRestrict;
  SRestrict.rt = RES_PROPERTY;
  SRestrict.res.resProperty.relop = RELOP_EQ;
  SRestrict.res.resProperty.ulPropTag = PR_ANR;
  SRestrict.res.resProperty.lpProp->ulPropTag = PR_ANR;
  SRestrict.res.resProperty.lpProp->Value.LPSZ = lpszName;
   
  ```

2. Call the contents table's [IMAPITable::Restrict](imapitable-restrict.md) method, passing the **SRestriction** structure as the  _lpRestriction_ parameter. 
    

