---
title: "IMAPIFolderSaveContentsSort"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFolder.SaveContentsSort
api_type:
- COM
ms.assetid: 5ae3fdf0-6193-4c1f-bd2e-d69c56d69773
description: "Last modified: July 23, 2011"
---

# IMAPIFolder::SaveContentsSort

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Sets the default sort order for a folder's contents table.
  
```
HRESULT SaveContentsSort(
  LPSSortOrderSet lpSortCriteria,
  ULONG ulFlags
);
```

## Parameters

 _lpSortCriteria_
  
> [in] A pointer to an [SSortOrderSet](ssortorderset.md) structure that contains the default sort order. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the default sort order is set. The following flag can be set:
    
RECURSIVE_SORT 
  
> The default sort order set applies to the indicated folder and to all its subfolders.
    
## Return value

S_OK 
  
> The sort order was successfully saved.
    
MAPI_E_NO_SUPPORT 
  
> The message store provider does not support saving a sort order for its folder contents tables.
    
## Remarks

The **IMAPIFolder::SaveContentsSort** method establishes a default sort order for a folder's contents table. That is, when a client calls the folder's [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method after the code calls **SaveContentsSort**, the rows in the returned contents table will appear in the order established by **SaveContentsSort**.
  
Not all message store providers support **SaveContentsSort**; it is acceptable for message store providers to return MAPI_E_NO_SUPPORT from the **SaveContentsSort** method. 
  
## See also

#### Reference

[IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md)
  
[SSortOrderSet](ssortorderset.md)
  
[IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md)

