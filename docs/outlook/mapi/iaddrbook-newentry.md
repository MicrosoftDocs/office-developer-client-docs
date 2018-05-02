---
title: "IAddrBookNewEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IAddrBook.NewEntry
api_type:
- COM
ms.assetid: 8d2d786b-e621-456d-b087-3373df6f8ac5
description: "Last modified: July 23, 2011"
---

# IAddrBook::NewEntry

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Adds a new recipient to an address book container or to the recipient list of an outgoing message.
  
```
HRESULT NewEntry(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  ULONG cbEIDContainer,
  LPENTRYID lpEIDContainer,
  ULONG cbEIDNewEntryTpl,
  LPENTRYID lpEIDNewEntryTpl,
  ULONG FAR * lpcbEIDNewEntry,
  LPENTRYID FAR * lppEIDNewEntry
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window for the dialog box.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the text that is used. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _cbEIDContainer_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEIDContainer_ parameter. 
    
 _lpEIDContainer_
  
> [in] A pointer to the entry identifier of the container where the new recipient is to be added. If the  _cbEIDContainer_ parameter is zero, the **NewEntry** method returns a recipient entry identifier and a list of templates as if the [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) method was called. 
    
 _cbEIDNewEntryTpl_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEIDNewEntryTpl_ parameter. 
    
 _lpEIDNewEntryTpl_
  
> [in] A pointer to a one-off template that will be used to create the new recipient. If  _cbEIDNewEntryTpl_ is zero and  _lpEIDNewEntryTpl_ is NULL, **NewEntry** displays a dialog box with which the user can select from a list of templates for adding new entries. 
    
 _lpcbEIDNewEntry_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEIDNewEntry_ parameter. 
    
 _lppEIDNewEntry_
  
> [out] A pointer to a pointer to the new recipient's entry identifier.
    
## Return value

S_OK 
  
> The new address book entry was successfully created.
    
## Remarks

The **NewEntry** method creates a new address book entry, to be added directly into a container or to be used to address an outgoing message. 
  
## Notes to Callers

If you want the new entry to be added to a specific container, set  _lpEIDContainer_ to the container's entry identifier and  _cbEIDContainer_ to the byte count in the entry identifier. 
  
If you want the new entry to be added to the recipient list of an outgoing message, set  _lpEIDContainer_ to NULL and  _cbEIDContainer_ to zero. 
  
If you want to allow the user of a client application to select the type of entry to be created, pass zero in  _cbEIDNewEntryTpl_ and NULL in  _lpEIDNewEntryTpl_. The **NewEntry** method displays the MAPI one-off table, a list of templates supported by MAPI and by each address book provider in the session. Each template can create a recipient entry for one or more address types. 
  
If you want to retain the entry identifier of the new entry, pass valid pointers in the  _lpcbEIDNewEntry_ and  _lppEIDNewEntry_ parameters. You are responsible for freeing this entry identifier when you are finished with it by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
To use a particular template to add a new entry to a modifiable container, use the following procedure:
  
1. Call the [IMAPISession::OpenEntry](imapisession-openentry.md) method to open the destination container, and set the  _lpEntryID_ parameter to the entry identifier of the container. 
    
2. Call the destination container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method, and set the  _ulPropTag_ parameter to **PR_CREATE_TEMPLATES** ( [PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) and the  _lpiid_ parameter to IID_IMAPITable. The container will return a one-off table that lists all the templates that it supports for creating new entries. 
    
3. Retrieve the row that represents the template for the particular type of entry you want to create. The **PR_ADDRTYPE** ( [PidTagAddressType](pidtagaddresstype-canonical-property.md)) column indicates the address type that is supported by the template.
    
4. Call the **NewEntry** method, and set  _lpEIDNewEntryTpl_ to the entry identifier of the selected template. The entry identifier will be the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) column from the template's row in the one-off table. Pass zero in  _cbEIDContainer_ and NULL in  _lpEIDContainer_. Pass a valid pointer in the  _lppEIDNewEntry_ parameter if you want to retain the new entry's entry identifier. 
    
## See also

#### Reference

[IAddrBook::OpenEntry](iaddrbook-openentry.md)
  
[IMAPIProp::OpenProperty](imapiprop-openproperty.md)
  
[PidTagCreateTemplates Canonical Property](pidtagcreatetemplates-canonical-property.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

