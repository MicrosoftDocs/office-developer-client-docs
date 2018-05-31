---
title: "Using an Advanced Search Dialog Box"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c9a156e6-3472-4409-a4ba-3a1a65b7bdcd
description: "Last modified: July 23, 2011"
 
 
---

# Using an Advanced Search Dialog Box

  
  
**Applies to**: Outlook 
  
Some address book containers support an advanced searching capability that allows clients to search on properties other than **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)). Address book containers that support advanced searches have a container object property called **PR_SEARCH** ([PidTagSearch](pidtagsearch-canonical-property.md)). This container object provides access to a display table that describes the search dialog box — a dialog box used to enter and edit the advanced search criteria.
  
 **To perform an advanced search on an address book container**
  
1. Call the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method, specifying **PR_SEARCH** for the property tag and IID_IMAPIContainer for the interface identifier. 
    
2. Call the search object 's **IMAPIProp::OpenProperty** method, specifying **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) for the property tag and IID_IMAPITable for the interface identifier. 
    
3. Call the search object's [IMAPIProp::SetProps](imapiprop-setprops.md) method to establish values for the properties to be used in the advanced search. 
    
4. Call the search object's [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to save the advanced search criteria. 
    
This sequence of calls results in a restriction being available when a client calls the search object's **GetSearchCriteria** method. 
  

