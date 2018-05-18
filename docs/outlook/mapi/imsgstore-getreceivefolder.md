---
title: "IMsgStoreGetReceiveFolder"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgStore.GetReceiveFolder
api_type:
- COM
ms.assetid: ccd9d623-a3cb-4e66-9649-78c3887cb726
description: "Last modified: March 09, 2015"
---

# IMsgStore::GetReceiveFolder

  
  
**Applies to**: Outlook 
  
Obtains the folder that was established as the destination for incoming messages of a specified message class or as the default receive folder for the message store.
  
```cpp
HRESULT GetReceiveFolder(
  LPSTR lpszMessageClass,
  ULONG ulFlags,
  ULONG FAR * lpcbEntryID,
  LPENTRYID FAR * lppEntryID,
  LPSTR FAR * lppszExplicitClass
);
```

## Parameters

 _lpszMessageClass_
  
> [in] A pointer to a message class that is associated with a receive folder. If the  _lpszMessageClass_ parameter is set to NULL or an empty string, **GetReceiveFolder** returns the default receive folder for the message store. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the passed-in and returned strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The message class string is in Unicode format. If the MAPI_UNICODE flag is not set, the message class string is in ANSI format.
    
 _lpcbEntryID_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier for the requested receive folder.
    
 _lppszExplicitClass_
  
> [out] A pointer to a pointer to the message class that explicitly sets as its receive folder the folder pointed to by  _lppEntryID_. This message class should either be the same as the class in the  _lpszMessageClass_ parameter, or a base class of that class. Passing NULL indicates that the folder pointed to by  _lppEntryID_ is the default receive folder for the message store. 
    
## Return value

S_OK 
  
> The receive folder was successfully returned.
    
## Remarks

The **IMsgStore::GetReceiveFolder** method obtains the entry identifier of a receive folder, a folder designated to receive incoming messages of a particular message class. Callers can specify a message class or NULL in the  _lpszMessageClass_ parameter. If  _lpszMessageClass_ is NULL, **GetReceiveFolder** returns the following values: 
  
- In  _lppszExplicitClass_, the name of the first base class of the message class pointed to by  _lpszMessageClass_ that does explicitly set a receive folder. 
    
- In  _lppEntryID_, the entry identifier of the receive folder for the base class pointed to by the  _lppszExplicitClass_ parameter. 
    
For example, suppose the receive folder of the message class **IPM.Note** has been set to the entry identifier of the Inbox and **GetReceiveFolder** is called with the contents of  _lpszMessageClass_ set to **IPM.Note.Phone**. If **IPM.Note.Phone** does not have an explicit receive folder set, **GetReceiveFolder** returns the entry identifier of the Inbox in  _lppEntryID_ and **IPM.Note** in  _lppszExplicitClass_.
  
If the client calls **GetReceiveFolder** for a message class and has not set a receive folder for that message class,  _lppszExplicitClass_ is either a zero-length string, a string in Unicode format, or a string in ANSI format depending on whether the client set the MAPI_UNICODE flag in the  _ulFlags_ parameter. 
  
A default receive folder, obtained by passing NULL in the  _lpszMessageClass_ parameter, always exists for every message store. 
  
A client should call the [MAPIFreeBuffer](mapifreebuffer.md) function when it is done with the entry identifier returned in  _lppEntryID_ to free the memory that holds that entry identifier. It should also call **MAPIFreeBuffer** when it is done with the message class string returned in  _lppszExplicitClass_ to free the memory that holds that string. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |GetInbox  <br/> |MFCMAPI uses the **IMsgStore::GetReceiveFolder** method to locate the Inbox folder.  <br/> |
   
## See also

#### Reference

[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

