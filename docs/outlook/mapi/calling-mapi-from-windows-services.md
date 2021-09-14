---
title: "Calling MAPI from Windows Services"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: debf7ec3-e9f9-4912-b9a2-fc0953a56a01
description: "Last modified: July 23, 2011"
 
 
---

# Calling MAPI from Windows Services

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
To enable MAPI client applications that are written as Windows services to operate with MAPI-compliant service providers, MAPI imposes several limitations and requirements.
  
MAPI clients have the following limitations:
  
- They cannot allow a user interface.
    
- They can send messages only through a tightly coupled message store and transport provider. In addition, MAPI clients can send and receive messages by using only the Microsoft Exchange Server or another server-based transport provider. Because of identity and security issues between client applications and the MAPI spooler, most transport providers are not supported in a service. 
    
All MAPI client applications, whether they are implemented as Windows services, must call the [MAPIInitialize](mapiinitialize.md) function to initialize the MAPI libraries. A call to the [OleInitialize](https://msdn.microsoft.com/library/ms690134%28v=VS.85%29.aspx) function is also necessary to use the OLE libraries. Both [MAPIInitialize](mapiinitialize.md) and [OleInitialize](https://msdn.microsoft.com/library/ms690134%28v=VS.85%29.aspx) make calls to the [CoInitialize](https://msdn.microsoft.com/library/ms678543%28VS.85%29.aspx) function to initialize the Component Object Model (COM) libraries. Clients that are services must set a special flag, MAPI_NT_SERVICE, in the **ulFlags** member of the [MAPIINIT_0](mapiinit_0.md) structure that is passed to [MAPIInitialize](mapiinitialize.md) and in the  _ulFlags_ parameter that is passed to the [MAPILogonEx](mapilogonex.md) function to inform MAPI of their special implementation. 
  
MAPI clients that are written as Windows services and written with the MAPI client interface have an additional requirement. They must set the MAPI_NO_MAIL flag in the call to [MAPILogonEx](mapilogonex.md). Other types of clients do not have to set a flag for logon because it is automatically set by MAPI.
  
To handle messages in an initialization thread, a MAPI client that is implemented as a service does the following:
  
1. Calls the [MsgWaitForMultipleObjects](https://msdn.microsoft.com/library/ms684242%28VS.85%29.aspx) function when the main thread blocks. 
    
2. Calls the [GetMessage](https://msdn.microsoft.com/library/ms644936%28VS.85%29.aspx), [TranslateMessage](https://msdn.microsoft.com/library/ms644955%28VS.85%29.aspx), and [DispatchMessage](https://msdn.microsoft.com/library/ms644934%28VS.85%29.aspx) sequence of Windows functions to handle the message when [MsgWaitForMultipleObjects](https://msdn.microsoft.com/library/ms684242%28VS.85%29.aspx) returns the sum of the value of the  _nCount_ parameter and the value of **WAIT_OBJECT_0**, which indicates that a message is in the queue.
    
## See also



[MAPIInitialize](mapiinitialize.md)
  
[MAPIINIT_0](mapiinit_0.md)
  
[MAPILogonEx](mapilogonex.md)


[Operating Environment Issues](operating-environment-issues.md)

