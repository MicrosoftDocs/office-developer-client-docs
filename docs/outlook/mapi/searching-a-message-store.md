---
title: "Searching a Message Store"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9e8d4639-7507-4d98-b56f-a65be369dc40
description: "Last modified: July 23, 2011"
 
 
---

# Searching a Message Store

  
  
**Applies to**: Outlook 
  
Client applications can search through one or more folders looking for messages that match search criteria. The most straightforward search technique involves applying a restriction to define criteria and placing the results into a search-results folder, created explicitly for this search or for a prior search. Not all message stores support this technique. To determine whether or not the message store you are using supports using search-results folders, call its [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) property. If the STORE_SEARCH_OK flag is set, searching is supported. If it is not set, you'll need an alternate approach such as manually inspecting the target folders.
  
 **To search one or more folders in a message store**
  
1. If you have a search-results folder from a previous search, skip to step 2. Otherwise, to create a search-results folder:
    
1. Retrieve the entry identifier for the search-results root folder by calling the message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method and requesting **PR_FINDER_ENTRYID** ([PidTagFinderEntryId](pidtagfinderentryid-canonical-property.md)).
    
2. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) to open the folder represented by PR_FINDER_ENTRYID. 
    
3. Call the folder's [IMAPIFolder::CreateFolder](imapifolder-createfolder.md) method to create a search-results folder with the FOLDER_SEARCH flag set. 
    
2. Build a restriction to hold your search criteria. 
    
3. Create an array of entry identifiers that represent the folders to search. This step is unnecessary if the search-results folder has been used before and you want to search the same folders.
    
4. Call the search-results folder's [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) method, pointing  _lpContainerList_ to the entry identifier array and  _lpRestriction_ to the restriction. 
    
5. If you have registered for search complete notifications with the message store, wait for the notification to arrive.
    
6. View the results of the search by calling the search-results folder's [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method to access its contents table. 
    
7. Call the contents table's [IMAPITable::QueryRows](imapitable-queryrows.md) method to retrieve the messages that satisfy the search criteria. 
    

