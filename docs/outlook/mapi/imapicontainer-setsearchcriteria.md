---
title: "IMAPIContainerSetSearchCriteria"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIContainer.SetSearchCriteria
api_type:
- COM
ms.assetid: b5eb1841-e450-4024-aeaa-3b5a492ddb99
description: "Last modified: March 09, 2015"
---

# IMAPIContainer::SetSearchCriteria

  
  
**Applies to**: Outlook 
  
Establishes search criteria for the container.
  
```
HRESULT SetSearchCriteria(
  LPSRestriction lpRestriction,
  LPENTRYLIST lpContainerList,
  ULONG ulSearchFlags
);
```

## Parameters

 _lpRestriction_
  
> [in] A pointer to an [SRestriction](srestriction.md) structure that defines the search criteria. If NULL is passed in the  _lpRestriction_ parameter, the search criteria that were used most recently for this container are used again. NULL should not be passed in  _lpRestriction_ for the first search in a container. 
    
 _lpContainerList_
  
> [in] A pointer to an array of entry identifiers that represent containers to be included in the search. If a client passes NULL in the  _lpContainerList_ parameter, the entry identifiers used most recently to search this container are used for the new search. A client should not pass NULL in  _lpContainerList_ for the first search in a container. 
    
 _ulSearchFlags_
  
> [in] A bitmask of flags that control how the search is performed. The following flags can be set:
    
BACKGROUND_SEARCH 
  
> The search should run at normal priority relative to other searches. This flag cannot be set at the same time as the FOREGROUND_SEARCH flag.
    
FOREGROUND_SEARCH 
  
> The search should run at high priority relative to other searches. This flag cannot be set at the same time as the BACKGROUND_SEARCH flag.
    
NON_CONTENT_INDEXED_SEARCH
  
> The search should not use content indexing to find matching entries. This flag is only valid for Exchange stores.
    
RECURSIVE_SEARCH 
  
> The search should include the containers specified in the  _lpContainerList_ parameter and all their child containers. This flag cannot be set at the same time as the SHALLOW_SEARCH flag. 
    
RESTART_SEARCH 
  
> The search should be initiated if this is the first call to **SetSearchCriteria**, or restarted if the search is inactive. This flag cannot be set at the same time as the STOP_SEARCH flag.
    
SHALLOW_SEARCH 
  
> The search should look only in the containers specified in the  _lpContainerList_ parameter for matching entries. This flag cannot be set at the same time as the RECURSIVE_SEARCH flag. 
    
STOP_SEARCH 
  
> The search should be stopped. This flag cannot be set at the same time as the RESTART_SEARCH flag.
    
## Return value

S_OK 
  
> The search criteria was successfully set.
    
MAPI_E_TOO_COMPLEX 
  
> The service provider does not support the specified search criteria.
    
## Remarks

The **IMAPIContainer::SetSearchCriteria** method establishes search criteria for a container that supports searches, typically a search-results folder. A search-results folder contains links to the messages that meet the search criteria; the actual messages are still stored in their original locations. The only unique data that is contained in a search-results folder is its contents table. The contents table of a search-results folder has the merged contents of the message store after the search restriction has been applied. 
  
A search operation works only on this merged contents table; it does not search through other search-results folders. The search results return only the messages that match the search criteria; the folder hierarchy is not returned.
  
Control is returned to the client when the search has finished.
  
## Notes to Implementers

Address book containers establish search criteria by applying restrictions to their contents tables. For more information about search criteria and address book containers, see [Implementing Advanced Searching](implementing-advanced-searching.md).
  
You should support open, copy, move, and delete operations on the messages within search-results folders, not on the search-results folder itself. Do not allow messages to be created within or copied into a search-results folder. 
  
## Notes to Callers

To search for message recipients, set  _lpRestriction_ to point to a subobject restriction with the **ulSubObject** member in the [SSubRestriction](ssubrestriction.md) structure set to **PR_MESSAGE_RECIPIENTS** ( [PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)). To search for attachments, set the **ulSubObject** member to **PR_MESSAGE_ATTACHMENTS** ( [PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)). Set the **lpRes** member to point to a property restriction that describes the search criteria for the recipients or attachments. 
  
For example, to look for file attachments that have the extension .mss, set **ulSubObject** to **PR_MESSAGE_ATTACHMENTS** and **lpRes** to a property restriction that matches **PR_ATTACH_EXTENSION** ( [PidTagAttachExtension](pidtagattachextension-canonical-property.md)) with .mss.
  
Setting the FOREGROUND_SEARCH flag in the  _ulSearchFlags_ parameter could cause a decrease in system performance. 
  
You can use **SetSearchCriteria** to change the search criteria of a search already in progress. You can specify new restrictions, new lists of folders to search, and a new search priority, such as upgrading a search to a higher priority. Changes in search priority do not cause an existing search to restart, but other changes to search criteria can. 
  
When you are through using a search-results folder, you can either delete the folder or let it remain open for later use. If you do delete the search-results folder, only message links are deleted. The actual messages remain in their parent folders. 
  
For more information about search-results folders, see [MAPI Search Folders](mapi-search-folders.md). 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|HierarchyTableDlg.cpp  <br/> |CHierarchyTableDlg::OnEditSearchCriteria  <br/> |MFCMAPI uses the **IMAPIContainer::SetSearchCriteria** method to write search criteria for a folder after a user has edited it.  <br/> |
   
## See also

#### Reference

[IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md)
  
[IMAPIContainer::OpenEntry](imapicontainer-openentry.md)
  
[IMAPIFolder::CreateFolder](imapifolder-createfolder.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)
  
[SPropertyRestriction](spropertyrestriction.md)
  
[SRestriction](srestriction.md)
  
[SSubRestriction](ssubrestriction.md)
  
[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

