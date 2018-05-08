---
title: "How to Manage a Message in an OST Without Invoking a Synchronization in Cached Exchange Mode"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 3a1f0aa2-813f-222c-f871-0501de5d9dec
description: "Last modified: July 23, 2011"
 
 
---

# How to: Manage a Message in an OST Without Invoking a Synchronization in Cached Exchange Mode

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
This topic contains a code sample in C++ that shows how to use  `IID_IMessageRaw` in **[IMsgStore::OpenEntry](imsgstore-openentry.md)** to obtain an **[IMessage](imessageimapiprop.md)** interface that manages a message in an offline folders file (OST) without forcing a download of the whole message when the client is in Cached Exchange Mode. 
  
When a client is in Cached Exchange Mode, messages in the OST can be in one of two states:
  
- The whole message that contains the header and the body is downloaded.
    
- The message with only its header is downloaded.
    
When you request an **IMessage** interface for a message in an OST and the client is in Cached Exchange Mode, use  `IID_IMessageRaw`. If you use  `IID_IMessage` to request an **IMessage** interface, and if the message has only its header downloaded in the OST, you invoke a synchronization that attempts to download the whole message. 
  
If you use  `IID_IMessageRaw` or  `IID_IMessage` to request an **IMessage** interface, the interfaces that are returned are identical in use. The **IMessage** interface that was requested by using  `IID_IMessageRaw` returns an email message as it exists in the OST, and synchronization is not forced. 
  
The following example shows how to call the **OpenEntry** method, passing  `IID_IMessageRaw` instead of  `IID_IMessage`.
  
```
HRESULT HrOpenRawMessage ( 
    LPMDB lpMSB,  
    ULONG cbEntryID,  
    LPENTRYID lpEntryID,  
    ULONG ulFlags,  
    LPMESSAGE* lpMessage) 
{ 
    ULONG ulObjType = NULL; 
 
    HRESULT hRes = lpMDB->OpenEntry( 
        cbEntryID, 
        lpEntryID, 
        IID_IMessageRaw, 
        ulFlags, 
        &amp;ulObjType, 
        (LPUNKNOWN*) lpMessage)); 
 
   return hRes; 
} 

```

If the **OpenEntry** method returns the **MAPI_E_INTERFACE_NOT_SUPPORTED** error code, it indicates that the message store does not support accessing the message in raw mode. In this situation, try the **OpenEntry** method again by passing  `IID_IMessage`.
  
## 

> [!IMPORTANT]
>  `IID_IMessageRaw` might not be defined in the downloadable header file that you currently have. In this case, you can add it to your code by using the following definition. Use the DEFINE_OLEGUID macro defined in the Microsoft Windows Software Development Kit (SDK) header file guiddef.h to associate the GUID symbolic name with its value. >  `#if !defined(INITGUID) || defined(USES_IID_IMessageRaw)`>  `DEFINE_OLEGUID(IID_IMessageRaw,0x0002038A, 0, 0);`>  `#endif`
  
## See also

#### Concepts

[About MAPI Additions](about-mapi-additions.md)
  
[How to: Access a Store on the Remote Server When Outlook is in Cached Exchange Mode](how-to-access-a-store-on-remote-server-when-outlook-is-in-cached-exchange-mode.md)
  
[How to: Open a Store on the Remote Server When Outlook is in Cached Exchange Mode](how-to-open-a-store-on-the-remote-server-when-outlook-is-in-cached-exchange-mode.md)

