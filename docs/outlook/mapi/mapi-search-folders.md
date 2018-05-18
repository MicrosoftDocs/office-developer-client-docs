---
title: "MAPI Search Folders"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 36c14d91-77f7-43a3-8d87-d50bcc21fad7
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Search Folders

  
  
**Applies to**: Outlook 
  
A search-results folder holds links to messages in generic folders rather than the actual messages. Clients create a search-results folder by calling the [IMAPIFolder::CreateFolder](imapifolder-createfolder.md) method with FOLDER_SEARCH as the  _ulFolderType_ parameter. Clients fill a search-results folder by setting up and applying search criteria — rules that filter out messages with particular characteristics. Search criteria are set up with the [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) method. Clients build one or more [SRestriction](srestriction.md) structures to represent the search criteria to be applied and pass them to **SetSearchCriteria**. **SetSearchCriteria** also specifies a list of folders that indicate the search domain and a set of flags that control how the search is performed. 
  
 **SetSearchCriteria** identifies the messages that match the specified restriction. The selected messages (the ones that satisfy the criteria) are displayed as links in the search-results folder. When the client calls the [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method to access the contents table of the search-results folder, the selected messages are displayed in the table. Contents tables for search-results folders contain the same columns as contents tables for generic folders. However, for search-results folders, the **PR_PARENT_ENTRYID** ([PidTagParentEntryId](pidtagparententryid-canonical-property.md)) property specifies the entry identifier of the folder where the linked message resides. Search-results folders are not considered parent folders.
  
Search-results folders have the following limits:
  
- The only way that the contents of a search-results folder can be modified is through a call to **SetSearchCriteria**. For more information about the implementation of **SetSearchCriteria**, see Knowledge Base article [260322: How To Search Folders with the SetSearchCriteria Method](http://go.microsoft.com/fwlink/?LinkId=123603).
    
- Messages cannot be moved or copied into search-results folders.
    
- Search-results folders cannot contain subfolders. 
    
- Clients cannot make a search-results folder the subject of a search.
    
It is possible, however, to modify the properties of a search-results folder and use it to delete a message. When a message is deleted from a search-results folder, it is actually deleted from the real folder. However, deleting the search-results folder itself has no impact on the messages inside; they remain in their generic folders.
  
## See also



[MAPI Folders](mapi-folders.md)

