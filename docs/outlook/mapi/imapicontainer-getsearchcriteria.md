---
title: "IMAPIContainerGetSearchCriteria"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIContainer.GetSearchCriteria
api_type:
- COM
ms.assetid: 41b6c162-9984-43a3-b38e-44f0afae67de
description: "Last modified: March 09, 2015"
---

# IMAPIContainer::GetSearchCriteria

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Obtains the search criteria for the container.
  
```
HRESULT GetSearchCriteria(
  ULONG ulFlags,
  LPSRestriction FAR * lppRestriction,
  LPENTRYLIST FAR * lppContainerList,
  ULONG FAR * lpulSearchState
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the passed-in strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lppRestriction_
  
> [out] A pointer to a pointer to an [SRestriction](srestriction.md) structure that defines the search criteria. If a client application passes NULL in the  _lppRestriction_ parameter, **GetSearchCriteria** does not return an **SRestriction** structure. 
    
 _lppContainerList_
  
> [out] A pointer to a pointer to an array of entry identifiers that represent containers to be included in the search. If a client passes NULL in the  _lppContainerList_ parameter, **GetSearchCriteria** does not return an array of entry identifiers. 
    
 _lpulSearchState_
  
> [out] A pointer to a bitmask of flags used to indicate the current state of the search. If a client passes NULL in the  _lpulSearchState_ parameter, **GetSearchCriteria** returns no flags. The following flags can be set: 
    
SEARCH_FOREGROUND 
  
> The search should run at high priority relative to other searches. If this flag is not set, the search runs at normal priority relative to other searches.
    
SEARCH_REBUILD 
  
> The search is in the CPU-intensive mode of its operation, trying to locate messages that match the criteria. If this flag is not set, the CPU-intensive part of the search's operation is over. This flag has meaning only if the search is active (that is, if the SEARCH_RUNNING flag is set).
    
SEARCH_RECURSIVE 
  
> The search is looking in specified containers and all their child containers for matching entries. If this flag is not set, only the containers explicitly included in the last call to the [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) method are being searched. 
    
SEARCH_RUNNING 
  
> The search is active and the container's contents table is being updated to reflect changes in the message store or address book. If this flag is not set, the search is inactive and the contents table is static.
    
## Return value

S_OK 
  
> The search criteria was successfully obtained.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_NOT_INITIALIZED 
  
> Search criteria were never established for the container.
    
## Remarks

The **IMAPIContainer::GetSearchCriteria** method obtains the search criteria for a container that supports searches, typically a search-results folder. You create search criteria by calling a container's **IMAPIContainer::SetSearchCriteria** method. 
  
## Notes to Implementers

Address book containers may need to support **GetSearchCriteria** only if they provide the advanced search capabilities associated with the **PR_SEARCH** ( [PidTagSearch](pidtagsearch-canonical-property.md)) property. For more information about how to implement the advanced search feature for address book containers, see [Implementing Advanced Searching](implementing-advanced-searching.md).
  
## Notes to Callers

When you are finished with the data structures pointed to by the  _lppRestriction_ and  _lppContainerList_ parameters, call [MAPIFreeBuffer](mapifreebuffer.md) once for each structure to be released. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|HierarchyTableDlg.cpp  <br/> |CHierarchyTableDlg::OnEditSearchCriteria  <br/> |MFCMAPI uses the **IMAPIContainer::GetSearchCriteria** method to obtain search criteria from a folder to display.  <br/> |
   
## See also

#### Reference

[IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md)
  
[IMAPIFolder::CreateFolder](imapifolder-createfolder.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagSearch Canonical Property](pidtagsearch-canonical-property.md)
  
[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

