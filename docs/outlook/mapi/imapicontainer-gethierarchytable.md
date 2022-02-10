---
title: "IMAPIContainerGetHierarchyTable"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIContainer.GetHierarchyTable
api_type:
- COM
ms.assetid: d0c54092-86a3-47e0-8133-72e119e74b65
description: "Last modified: March 09, 2015"
---

# IMAPIContainer::GetHierarchyTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer to the container's hierarchy table.
  
```cpp
HRESULT GetHierarchyTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how information is returned in the table. The following flags can be set:
    
CONVENIENT_DEPTH 
  
> Fills the hierarchy table with containers from multiple levels. If CONVENIENT_DEPTH is not set, the hierarchy table contains only the container's immediate child containers.
    
MAPI_DEFERRED_ERRORS 
  
> **GetHierarchyTable** can return successfully, possibly before the table is made available to the caller. If the table is not available, making a subsequent table call can raise an error. 
    
MAPI_UNICODE 
  
> Requests that the columns that contain string data be returned in Unicode format. If the MAPI_UNICODE flag is not set, the strings should be returned in ANSI format. 
    
SHOW_SOFT_DELETES
  
> Shows items that are currently marked as soft deleted—that is, they are in the deleted item retention time phase.
    
 _lppTable_
  
> [out] A pointer to a pointer to the hierarchy table.
    
## Return value

S_OK 
  
> The hierarchy table was successfully retrieved.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_NO_SUPPORT 
  
> The container has no child containers and cannot provide a hierarchy table.
    
## Remarks

The **IMAPIContainer::GetHierarchyTable** method returns a pointer to the hierarchy table of a container. A hierarchy table holds summary information about the child containers in the container. Folder hierarchy tables hold information about subfolders; address book hierarchy tables hold information about child address book containers and distribution lists. 
  
It is possible for some containers to have no child containers. These containers return MAPI_E_NO_SUPPORT from their implementations of **GetHierarchyTable**.
  
When the CONVENIENT_DEPTH flag is set, each row in the hierarchy table also includes the **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md)) property as a column. **PR_DEPTH** indicates the level of each container relative to the container that implements the table. The implementing container's immediate child containers are at depth zero, child containers in the zero depth containers are at depth one, and so on. The values of **PR_DEPTH** increase sequentially as the hierarchy of levels deepens. 
  
For a complete list of required and optional columns in hierarchy tables, see [Hierarchy Tables](hierarchy-tables.md).
  
## Notes to implementers

If you support a hierarchy table for your container, you must also do the following:
  
- Support a call to the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_CONTAINER_HIERARCHY** ([PidTagContainerHierarchy](pidtagcontainerhierarchy-canonical-property.md)) property.
    
- Return **PR_CONTAINER_HIERARCHY** from a call to the container's [IMAPIProp::GetPropList](imapiprop-getproplist.md) or [IMAPIProp::GetProps](imapiprop-getprops.md) methods. 
    
## Notes to callers

String and binary contents table columns can be truncated. Typically, providers return 255 characters. Because you cannot know beforehand whether a table includes truncated columns, assume that a column is truncated if the length of the column is either 255 or 510 bytes. You can always retrieve the full value of a truncated column, if necessary, directly from the object by using its entry identifier to open it and then calling the [IMAPIProp::GetProps](imapiprop-getprops.md) method. 
  
Depending on the provider's implementation, restrictions and sorting operations can apply to the whole string or to the truncated version of that string. Moreover, store providers are not guaranteed to honor the sort order set [SSortOrderSet](ssortorderset.md) specified for hierarchy tables. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|HierarchyTableTreeCtrl.cpp  <br/> |CHierarchyTableTreeCtrl::GetHierarchyTable  <br/> |The CHierarchyTableTreeCtrl class uses **GetHierarchyTable** to obtain hierarchy tables to display in a tree view control. |
   
## See also



[IMAPIProp::GetPropList](imapiprop-getproplist.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
  
[PidTagContainerHierarchy Canonical Property](pidtagcontainerhierarchy-canonical-property.md)
  
[IMAPIContainer : IMAPIProp](imapicontainerimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

