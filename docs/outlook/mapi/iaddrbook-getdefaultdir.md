---
title: "IAddrBookGetDefaultDir"
description: The IAddrBookGetDefaultDir function returns the entry identifier for the initial address book container. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.GetDefaultDir
api_type:
- COM
ms.assetid: 7a9fdf3f-fd76-40fb-8217-967c6efba5f6
---

# IAddrBook::GetDefaultDir

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the entry identifier for the initial address book container.
  
```cpp
HRESULT GetDefaultDir(
  ULONG FAR * lpcbEntryID,
  LPENTRYID FAR * lppEntryID
);
```

## Parameters

 _lpcbEntryID_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier of the default container.
    
## Return value

S_OK 
  
> The entry identifier of the default container was successfully returned.
    
## Remarks

Client applications and service providers call the **GetDefaultDir** method to retrieve the entry identifier of the default address book container. The default container is what the user sees displayed in the address book when the address book is first opened. If a default container has not been set by a call to the [IAddrBook::SetDefaultDir](iaddrbook-setdefaultdir.md) method, MAPI assigns as the default container the first container with names that is not the personal address book (PAB). If such a container cannot be found, the PAB becomes the default container. 
  
To set the default directory, a client or provider calls the **SetDefaultDir** method. Clients and providers do not have to call the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method; because changes to the address book are not transacted, changes are immediately made permanent. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnOpenDefaultDir  <br/> |MFCMAPI uses the **GetDefaultDir** method to get the ID for the default address book container. |
   
## See also



[IAddrBook::SetDefaultDir](iaddrbook-setdefaultdir.md)
  
[MAPIAllocateBuffer](mapiallocatebuffer.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagContainerFlags Canonical Property](pidtagcontainerflags-canonical-property.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

