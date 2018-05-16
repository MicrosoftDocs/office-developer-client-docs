---
title: "IMAPISupportCreateOneOff"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.CreateOneOff
api_type:
- COM
ms.assetid: ee57d6e0-9de0-4427-97ce-371c1c01f3de
description: "Last modified: July 23, 2011"
---

# IMAPISupport::CreateOneOff

  
  
**Applies to**: Outlook 
  
Creates an entry identifier for a one-off address.
  
```
HRESULT CreateOneOff(
  LPSTR lpszName,
  LPSTR lpszAdrType,
  LPSTR lpszAddress,
  ULONG ulFlags,
  ULONG FAR * lpcbEntryID,
  LPENTRYID FAR * lppEntryID
);
```

## Parameters

 _lpszName_
  
> [in] A pointer to the display name of the recipient the **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property. The  _lpszName_ parameter can be NULL. 
    
 _lpszAdrType_
  
> [in] A pointer to the address type (such as FAX, SMTP, or X500) of the recipient. The  _lpszAdrType_ parameter cannot be NULL. 
    
 _lpszAddress_
  
> [in] A pointer to the messaging address of the recipient. The  _lpszAddress_ parameter cannot be NULL. 
    
 _ulFlags_
  
> [in] A bitmask of flags that affects the one-off recipient. The following flags can be set:
    
MAPI_SEND_NO_RICH_INFO 
  
> The recipient cannot handle formatted message content. If MAPI_SEND_NO_RICH_INFO is set, MAPI sets the recipient's **PR_SEND_RICH_INFO** ( [PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) property to FALSE. If MAPI_SEND_NO_RICH_INFO is not set, MAPI sets this property to TRUE unless the recipient's messaging address pointed to by  _lpszAddress_ is interpreted to be an Internet address. In this case, MAPI sets **PR_SEND_RICH_INFO** to FALSE. 
    
MAPI_UNICODE 
  
> The display name, address type, and address are in Unicode format. If the MAPI_UNICODE flag is not set, these strings are in ANSI format.
    
 _lpcbEntryID_
  
> [out] A pointer to the count of bytes in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier for the one-off recipient.
    
## Return value

S_OK 
  
> The one-off entry identifier was successfully created.
    
## Remarks

The **IMAPISupport::CreateOneOff** method is implemented for all service provider support objects. Service providers call **CreateOneOff** to create an entry identifier for a one-off recipient (a recipient that does not belong to any of the containers from any of the currently loaded address book providers). 
  
## Notes to Callers

When you are finished using the entry identifier returned by **CreateOneOff**, free the memory allocated for the entry identifier by using the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## Notes to Transport Providers

Support the Transport Neutral Encapsulation Format (TNEF) and use the value of the **PR_SEND_RICH_INFO** property to determine whether to use TNEF when you transport a message. Not supporting TNEF or not sending a message in this format when it is requested can be a problem for form-based clients or clients that require custom MAPI properties. This is because TNEF is typically used to send custom properties for custom message classes. 
  
## See also

#### Reference

[MAPIFreeBuffer](mapifreebuffer.md)
  
[PidTagDisplayName Canonical Property](pidtagdisplayname-canonical-property.md)
  
[PidTagSendRichInfo Canonical Property](pidtagsendrichinfo-canonical-property.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

