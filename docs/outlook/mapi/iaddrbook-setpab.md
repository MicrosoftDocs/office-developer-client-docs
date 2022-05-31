---
title: "IAddrBookSetPAB"
description: This article describes the IAddrBookSetPAB function and  provides syntax, parameters, return value, and additional remarks.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.SetPAB
api_type:
- COM
ms.assetid: 75daf9d4-6975-435f-91e5-1b41e0047ab7
---

# IAddrBook::SetPAB

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Designates a particular container as the personal address book (PAB).
  
```cpp
HRESULT SetPAB(
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the container to be designated as the PAB. The  _lpEntryID_ parameter cannot be NULL. 
    
## Return value

S_OK 
  
> The specified container has been established as the PAB.
    
## Remarks

Clients and service providers call the **SetPAB** method to designate a particular container as the PAB. The PAB is a container that consists of entries copied from other containers as well as new entries. 
  
A call to **SetPAB** establishes a container as the PAB until that container is made unavailable or a new container becomes the PAB through a subsequent call to **SetPAB**. 
  
Clients and providers do not have to call the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method to make the PAB change permanent. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|AbContDlg.cpp  <br/> |CAbContDlg::OnSetPAB  <br/> |MFCMAPI uses the **SetPAB** method to make the specified container the PAB. |
   
## See also



[IAddrBook::GetPAB](iaddrbook-getpab.md)
  
[IAddrBook::GetSearchPath](iaddrbook-getsearchpath.md)
  
[PidTagContainerFlags Canonical Property](pidtagcontainerflags-canonical-property.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

