---
title: "IAddrBookGetPAB"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.GetPAB
api_type:
- COM
ms.assetid: 9830e09c-700f-469b-a54d-4e4e0583aa84
description: "Last modified: March 09, 2015"
---

# IAddrBook::GetPAB

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the entry identifier of the container that is designated as the personal address book (PAB).
  
```cpp
HRESULT GetPAB(
  ULONG FAR * lpcbEntryID,
  LPENTRYID FAR * lppEntryID
);
```

## Parameters

 _lpcbEntryID_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier of the PAB. The  _lppEntryID_ parameter contains zero if no container has been designated as the PAB. 
    
## Return value

S_OK 
  
> The entry identifier of the PAB was successfully returned.
    
## Remarks

Clients call the **GetPAB** method to retrieve the entry identifier of the container designated as the PAB. If a PAB has not been established in the profile, MAPI selects as the PAB the first container in the address book hierarchy that allows modifications. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnOpenPAB  <br/> |MFCMAPI uses the **GetPAB** method to get the ID for the user's personal address book.  <br/> |
   
## See also



[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagContainerFlags Canonical Property](pidtagcontainerflags-canonical-property.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

