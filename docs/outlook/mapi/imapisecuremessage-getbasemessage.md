---
title: "IMAPISecureMessageGetBaseMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISecureMessage.GetBaseMessage
api_type:
- COM
ms.assetid: 573f40c5-e0d2-4281-8c22-10a1ae1f0dee
description: "Last modified: July 23, 2011"
---

# IMAPISecureMessage::GetBaseMessage

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Retrieves the underlying [IMessage : IMAPIProp](imessageimapiprop.md) that this [IMAPISecureMessage : IUnknown](imapisecuremessageiunknown.md) is encapsulating. 
  
```
HRESULT GetBaseMessage(
  LPMMESSAGE FAR * ppmsg
);
```

## Parameters

 _ppmsg_
  
> [out] A secure message object.
    
## Return value

S_OK
  
> The call succeeded and has returned the expected value or values.
    
## See also

#### Reference

[IMAPISecureMessage : IUnknown](imapisecuremessageiunknown.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)

