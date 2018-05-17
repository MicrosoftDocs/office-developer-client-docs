---
title: "Comparing Address Book Entries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e375367b-d107-4768-95de-00b8b9dc3511
description: "Last modified: July 23, 2011"
 
 
---

# Comparing Address Book Entries

  
  
**Applies to**: Outlook 
  
Your provider's [IABLogon::CompareEntryIDs](iablogon-compareentryids.md) implementation compares the entry identifiers for two of your provider's objects. MAPI calls this method after determining that the two entry identifiers contain your provider's registered [MAPIUID](mapiuid.md). Therefore, your **CompareEntryIDs** method need not check that the entry identifiers passed in for the  _lpEntryID1_ and  _lpEntryID2_ parameters belong to your provider. 
  
Calling **IABLogon::CompareEntryIDs** is equivalent to retrieving the **PR_RECORD_KEY** ( [PidTagRecordKey](pidtagrecordkey-canonical-property.md)) property for each of the two objects and comparing them directly.
  
 **To implement CompareEntryIds**
  
1. Check the type of the entry identifiers passed in if your provider stores that information. For example, one entry identifier might belong to a messaging user while the other might belong to a distribution list. If the types do not match, set the contents of the  _lpulResult_ parameter to FALSE and return. 
    
2. Compare the sizes of the two entry identifiers. If they are not the same, set the contents of the  _lpulResult_ parameter to FALSE and return. 
    
3. Check that the size of the entry identifiers is the correct size for their type. If not, set the contents of the  _lpulResult_ parameter to FALSE and return the error value MAPI_E_UNKNOWN_ENTRYID. 
    
4. Check if the entry identifiers are the same. If they compare equally, set the contents of the  _lpulResult_ parameter to TRUE and return. Otherwise, set it to FALSE before returning. 
    
5. If your provider is comparing a short-term entry identifier with a long-term identifier, they should compare equally.
    

