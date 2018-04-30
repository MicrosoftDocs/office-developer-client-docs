---
title: "Implementing Name Resolution"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: a4c71b08-c47a-4421-8603-d5356d32dca9
description: "Last modified: July 23, 2011"
---

# Implementing Name Resolution

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Address book providers are responsible for supporting name resolution — the process of associating an entry identifier with a display name. Clients initiate name resolution when they call [IAddrBook::ResolveName](iaddrbook-resolvename.md) to ensure that each member of an outgoing message's recipient list corresponds to a valid address. 
  
Your provider can support name resolution by:
  
- Supporting the **PR_ANR** ( [PidTagAnr](pidtaganr-canonical-property.md)) property restriction, a requirement for all address book containers.
    
- Implementing the [IABContainer::ResolveNames](iabcontainer-resolvenames.md) method, an option for all address book containers. 
    
If you choose to support **IABContainer::ResolveNames**, attempt to locate an exact match for each unresolved display name in the [ADRLIST](adrlist.md) structure passed in with the  _lpAdrList_ parameter. You can identifiy an unresolved display name because it is missing the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property in the property value array in its **aEntries** member of the **ADRLIST** structure. Ignore any entries that have zero properties associated with them. 
  
Report the result of your attempt at resolution in the  _lpFlagList_ parameter, an array of flags that corresponds to the array of display names in  _lpAdrList_. The flags are positional such that the first flag corresponds to the first **aEntries** member in the **ADRLIST** structure, the second flag corresponds to the second **aEntries** member, and so on. 
  
There are three possible results for each unresolved entry:
  
- No match was found, meaning that none of the entries in your container entries match the entry in the **ADRLIST** structure. Set the corresponding entry in the  _lpFlagList_ parameter to MAPI_UNRESOLVED. 
    
- Several matches can be found, meaning that there are multiple container entries that match the entry in the **ADRLIST** structure. Set the corresponding entry in the  _lpFlagList_ parameter to MAPI_AMBIGUOUS. Do not change the number of entries in the **ADRLIST** structure. 
    
- An exact match can be found, meaning that there is only one container entry that matches the entry in the **ADRLIST** structure. Set the corresponding member in the  _lpFlagList_ parameter to MAPI_RESOLVED and add the entry identifier to the array of properties associated with the **ADRLIST** entry. 
    
If you choose not to support **IABContainer::ResolveNames**, return MAPI_E_NO_SUPPORT from your implementation.
  
All address book providers are required to support ambiguous name resolution — the **PR_ANR** property restriction — on their containers' contents tables. To provide this support, handle the PR_ANR restriction in your implementation of [IMAPITable::Restrict](imapitable-restrict.md) by performing a "best guess" type of search, matching against one or more particular properties that make sense for your provider. You can choose to use the same property or properties every time, such as **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) or **PR_ACCOUNT** ( [PidTagAccount](pidtagaccount-canonical-property.md)), or allow an administrator to choose from a list of acceptable properties. 
  
Although most providers supply their own contents table implementation, you can customize the implementation supplied by MAPI through the [CreateTable](createtable.md) function. However, because the MAPI implementation does not support restrictions of any kind, you must create a wrapper object to include a customized version of **Restrict** that intercepts the call. 
  

