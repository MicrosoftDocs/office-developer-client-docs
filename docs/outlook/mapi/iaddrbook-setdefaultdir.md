---
title: "IAddrBookSetDefaultDir"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.SetDefaultDir
api_type:
- COM
ms.assetid: d5d60150-15e4-41ff-bfb0-0c67e2abcacc
description: "Last modified: March 09, 2015"
---

# IAddrBook::SetDefaultDir

  
  
**Applies to**: Outlook 
  
Establishes the specified container as the default address book container.
  
```cpp
HRESULT SetDefaultDir(
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the default address book container.
    
## Return value

S_OK 
  
> The default address book container was successfully set.
    
## Remarks

Clients and service providers call the **SetDefaultDir** method to establish a new default address book container. The default container is the container that the user sees displayed in the address book when the address book is first opened. **SetDefaultDir** saves the default container as an entry in the profile. The container remains as the default until either another call to **SetDefaultDir** is made in the same session or in another session, or the container is removed. 
  
> [!NOTE]
> The [PR_AB_CHOOSE_DIRECTORY_AUTOMATICALLY](pidtagaddressbookchoosedirectoryautomatically-canonical-property.md) property corresponds to the **Choose automatically** setting in the Address Book Options dialog. When this property exists in the [IID_CAPONE_PROF](http://msdn.microsoft.com/library/281aabc3-9656-299c-4c78-7733dc71050a%28Office.15%29.aspx) profile section and is set to **true**, the Address Book dialog no longer defaults to the container specified by **SetDefaultDir**, but chooses an address book that Microsoft Outlook considers appropriate for the context in which the dialog was displayed. Note that this may result in a poor experience for third-party address book providers. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|Abcontdlg.cpp  <br/> |CAbContDlg::OnSetDefaultDir  <br/> |MFCMAPI uses the **SetDefaultDir** method to make the specified address book container the default one.  <br/> |
   
## See also



[IAddrBook::GetDefaultDir](iaddrbook-getdefaultdir.md)
  
[IAddrBook::GetSearchPath](iaddrbook-getsearchpath.md)
  
[IMAPISession::Logoff](imapisession-logoff.md)
  
[MAPILogonEx](mapilogonex.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

