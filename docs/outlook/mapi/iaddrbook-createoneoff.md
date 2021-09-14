---
title: "IAddrBookCreateOneOff"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.CreateOneOff
api_type:
- COM
ms.assetid: bcacfbdf-edff-4810-a985-e6d2c9271901
description: "Last modified: March 09, 2015"
---

# IAddrBook::CreateOneOff

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates an entry identifier for a one-off address.
  
```cpp
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
  
> [in] A pointer to the value of the recipient's **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property. The  _lpszName_ parameter can be NULL. 
    
 _lpszAdrType_
  
> [in] A pointer to the address type of the recipient, such as FAX or SMTP. The  _lpszAdrType_ parameter cannot be NULL. 
    
 _lpszAddress_
  
> [in] A pointer to the address of the recipient. The  _lpszAddress_ parameter cannot be NULL. 
    
 _ulFlags_
  
> [in] A bitmask of flags that affects the one-off recipient. The following flags can be set:
    
MAPI_SEND_NO_RICH_INFO 
  
> The recipient cannot handle formatted message content. If MAPI_SEND_NO_RICH_INFO is set, MAPI sets the recipient's **PR_SEND_RICH_INFO** ([PidTagSendRichInfo](pidtagsendrichinfo-canonical-property.md)) property to FALSE. If MAPI_SEND_NO_RICH_INFO is not set, MAPI sets this property to TRUE unless the recipient's messaging address pointed to by  _lpszAddress_ is interpreted to be an Internet address. In this case, MAPI sets **PR_SEND_RICH_INFO** to FALSE. 
    
MAPI_UNICODE 
  
> The display name, address type, and address are in Unicode format. If the MAPI_UNICODE flag is not set, these strings are in ANSI format.
    
 _lpcbEntryID_
  
> [out] A pointer to the byte count in the entry identifier pointed to by the  _lppEntryID_ parameter. 
    
 _lppEntryID_
  
> [out] A pointer to a pointer to the entry identifier for the one-off recipient.
    
## Return value

S_OK 
  
> The one-off entry identifier was created successfully.
    
## Remarks

Clients call the **CreateOneOff** method to create an entry identifier for a one-off recipient — a recipient that does not belong to any of the containers from any of the currently loaded address book providers. One-off recipients can have any kind of address that is supported by one of the active address book providers for the session. 
  
One-off recipients are typically created with a template for their particular address type. The address book provider that supports the address type supplies the template. A user of a client application enters the relevant information into the template.
  
MAPI supports Unicode character strings for the display name, address type, and address parameters of **CreateOneOff**.
  
The MAPI_SEND_NO_RICH_INFO flag controls whether formatted text in Rich Text Format (RTF) is sent along with each message. The Transport Neutral Encapsulation Format (TNEF) — a format that is used for transmitting formatted text — is sent by most transport providers, regardless of how the recipient sets its **PR_SEND_RICH_INFO** property. This is not an issue for messaging clients that work with interpersonal messages. However, because TNEF is typically used to send custom properties for custom message classes, not supporting it can be a problem for form-based clients or clients that require custom MAPI properties. For more information, see [Sending Messages with TNEF](sending-messages-with-tnef.md).
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|Mapiabfunctions.cpp  <br/> |AddOneOffAddress  <br/> |MFCMAPI uses the **CreateOneOff** method to create an entry ID for an address that is not found in any address book.  <br/> |
   
## See also



[IMAPISupport::CreateOneOff](imapisupport-createoneoff.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

