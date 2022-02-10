---
title: "IMsgStoreSetReceiveFolder"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgStore.SetReceiveFolder
api_type:
- COM
ms.assetid: 469f0412-1343-47ce-b6e8-e0d5e56c29bb
description: "Last modified: March 09, 2015"
---

# IMsgStore::SetReceiveFolder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Establishes a folder as the destination for incoming messages of a particular message class.
  
```cpp
HRESULT SetReceiveFolder(
  LPSTR lpszMessageClass,
  ULONG ulFlags,
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _lpszMessageClass_
  
> [in] A pointer to the message class that is to be associated with the new receive folder. If the  _lpszMessageClass_ parameter is set to NULL or an empty string, **SetReceiveFolder** sets the default receive folder for the message store. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text in the passed-in strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The message class string is in Unicode format. If the MAPI_UNICODE flag is not set, the message class string is in ANSI format.
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the folder to establish as the receive folder. If the  _lpEntryID_ parameter is set to NULL, **SetReceiveFolder** replaces the current receive folder with the message store's default. 
    
## Return value

S_OK 
  
> A receive folder was successfully established.
    
## Remarks

The **IMsgStore::SetReceiveFolder** method sets or changes the receive folder for a particular message class. With **SetReceiveFolder**, a client can, by using successive calls, specify a different receive folder for each defined message class or specify that incoming messages for multiple message classes all go to the same folder. For example, a client can have its own class of messages arrive in its own folder. A fax application can designate one folder in which the store provider puts incoming faxes and another folder in which the provider puts outgoing faxes.
  
If an error occurs during the call to **SetReceiveFolder**, the receive folder setting remains unchanged. 
  
If **SetReceiveFolder** changes the receive folder setting with  _lpEntryID_ set to NULL, indicating that the default receive folder should be set, **SetReceiveFolder** returns S_OK even if there was no existing setting for the indicated message class. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgStoreDlg.cpp  <br/> |CMsgStoreDlg::OnSetReceiveFolder  <br/> |MFCMAPI uses the **IMsgStore::SetReceiveFolder** method to set a folder as the receive folder for a particular message class. |
   
## See also



[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

