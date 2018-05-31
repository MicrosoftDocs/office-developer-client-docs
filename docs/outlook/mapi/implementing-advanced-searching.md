---
title: "Implementing Advanced Searching"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 08cc60d4-cac8-4ba5-bd7f-a56e63697be3
description: "Last modified: July 23, 2011"
 
 
---

# Implementing Advanced Searching

  
  
**Applies to**: Outlook 
  
Some address book containers support an advanced searching capability that allows clients to search on properties other than **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)). To support advanced searches, your provider must implement a special container that is accessible through the **PR_SEARCH** ([PidTagSearch](pidtagsearch-canonical-property.md)) property of your other containers. **PR_SEARCH** contains a container object that provides access to a display table that describes the dialog box used to enter and edit the advanced search criteria. 
  
 **To support advanced searching**
  
1. Define a property for each of your search criteria.
    
2. In the section of code in your container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method that handles the **PR_SEARCH** property: 
    
1. Check that the client is requesting the **IMAPIContainer** interface. If an inappropriate interface is being requested, fail and return MAPI_E_INTERFACE_NOT_SUPPORTED. 
    
2. Create a new search object that supports the **IMAPIContainer** interface. 
    
3. At this point, a call will be made to your search container's **IMAPIProp::OpenProperty** method to retrieve its **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property. Your provider must supply a display table, typically through a call to [BuildDisplayTable](builddisplaytable.md), that describes the container's advanced search dialog box.
    
4. MAPI displays the search dialog box, allowing the user to enter the appropriate criteria. When the user has finished, MAPI calls the container's [IMAPIProp::SetProps](imapiprop-setprops.md) method to store the search criteria. 
    
5. A call will be made to request your search container's contents table. Populate the contents table with all of the entries in the container that match the criteria.
    

