---
title: "HrValidateIPMSubtree" 
manager: lindalu
ms.date: 02/06/2022
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.HrValidateIPMSubtree
api_type:
- COM
ms.assetid: 6454c1fa-5216-4934-a908-48c634ac4a07
---

# HrValidateIPMSubtree  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adds standard interpersonal message (IPM) folders to a message store. 
  
|Property |Value |
|:-----|:-----|
|Header file: |Mapiutil.h |
|Implemented by: |MAPI |
|Called by: |Client applications |
   
```cpp
HrValidateIPMSubtree(
  LPMDB lpMDB,
  ULONG ulFlags,
  ULONG FAR * lpcValues,
  LPSPropValue FAR * lppProps,
  LPMAPIERROR FAR * lppMapiError
);
```

## Parameters

 _lpMDB_
  
> [in] Pointer to the message store object to which to add the folders. 
    
 _ulFlags_
  
> [in] Bitmask of flags used to control how the folders are created. The following flags can be set:
    
MAPI_FORCE_CREATE 
  
> The folders should be verified before creation, even if message store properties indicate that they are valid. A client application typically sets this flag when an error indicates that the structure of an existing folder has been damaged. 
    
MAPI_FULL_IPM_TREE 
  
> The full set of IPM folders should be created in the message store's root folder. The folder titles in the hierarchy are:
    
 - Folder Views
 - Common Views
 - Search Root\*
 - IPM Subtree\*
 - Inbox
 - Outbox
 - Deleted Items\*
 - Sent Items
    
where the three folders marked with \* are the minimum set created even when the MAPI_FULL_IPM_TREE flag has not been set. A client application typically sets this flag when the message store in which the folders are to be created is the default store.
    
 _lpcValues_
  
> [in, out] Pointer to the number of [SPropValue](spropvalue.md) structures in the array returned in the _lppProps_ parameter. The value of the  _lpcValues_ parameter can be zero if  _lppProps_ is NULL. 
    
 _lppProps_
  
> [in, out] Pointer to a pointer to an array of **SPropValue** structures that contains property values for the **PR_VALID_FOLDER_MASK** ([PidTagValidFolderMask](pidtagvalidfoldermask-canonical-property.md)) property and for the appropriate folder entry identifier properties. If **HrValidateIPMSubtree** creates an Inbox in the message store, the **SPropValue** array includes an Inbox entry identifier with a special property tag coded as  `PROP_TAG(PT_BINARY, PROP_ID_NULL)`. The  _lppProps_ parameter can be NULL, indicating that the calling implementation does not require that an **SPropValue** array be returned. 
    
 _lppMapiError_
  
> [out] Pointer to a pointer to a [MAPIERROR](mapierror.md) structure that contains version, component, and context information for an error. The  _lppMAPIError_ parameter is set to NULL if no **MAPIERROR** structure is returned. 
    
## Return value

None.
  
## Remarks

MAPI uses the **HrValidateIPMSubtree** function internally to construct the standard IPM subtree in a message store when the store is first opened, or when a store is made the default store. This function can also be used by client applications to validate or repair standard message folders. 
  
 **HrValidateIPMSubtree** always creates the Search Root and IPM Subtree folders in the store's root folder and the Deleted Items folder in the IPM Subtree folder. The IPM Subtree folder is the root of the IPM hierarchy in that message store. The Search Root folder can be used as the root of a subtree for search-results folders. 
  
IPM clients should display their folder view starting at the IPM subtree root folder and showing child folders beneath it. Information in the root folder of a message store should not appear in a client's user interface. This functionality means that if a client must hide information, the information can be put in the IPM subtree root directory, where it is not visible to the user. In contrast, non-IPM applications that require messages and folders to be invisible to the user, for example in a server-based message store, can put them outside the IPM hierarchy. 
  
 **HrValidateIPMSubtree** sets the **PR_VALID_FOLDER_MASK** property to indicate whether each IPM folder it creates has a valid entry identifier. The following entry identifier properties of the message store are set to the entry identifiers of the corresponding folders and returned in the _lppProps_ parameter along with **PR_VALID_FOLDER_MASK**: 
  
> **PR_COMMON_VIEWS_ENTRYID** ([PidTagCommonViewsEntryId](pidtagcommonviewsentryid-canonical-property.md))
  
> **PR_FINDER_ENTRYID** ([PidTagFinderEntryId](pidtagfinderentryid-canonical-property.md))
  
> **PR_IPM_OUTBOX_ENTRYID** ([PidTagIpmOutboxEntryId](pidtagipmoutboxentryid-canonical-property.md))
  
> **PR_IPM_SENTMAIL_ENTRYID** ([PidTagIpmSentMailEntryId](pidtagipmsentmailentryid-canonical-property.md))
  
> **PR_IPM_SUBTREE_ENTRYID** ([PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md))
  
> **PR_IPM_WASTEBASKET_ENTRYID** ([PidTagIpmWastebasketEntryId](pidtagipmwastebasketentryid-canonical-property.md))
  
> **PR_VIEWS_ENTRYID** ([PidTagViewsEntryId](pidtagviewsentryid-canonical-property.md))
  
> A placeholder [PROP_TAG](prop_tag.md) for the IPM Inbox (PT_BINARY, PROP_ID_NULL). 
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MstStoreDlg.cpp |CMsgStoreDlg::OnValidateIPMSubtree |MFCMAPI uses the **HrValidateIPMSubtree** method to add standard folders to a message store. |
   
## See also

[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
