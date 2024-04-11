---
title: "IMAPISecureMessageGetBaseMessage"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISecureMessage.GetBaseMessage
api_type:
- COM
ms.assetid: 573f40c5-e0d2-4281-8c22-10a1ae1f0dee
---

# IMAPISecureMessage::GetBaseMessage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves the underlying [IMessage : IMAPIProp](imessageimapiprop.md) that this [IMAPISecureMessage : IUnknown](imapisecuremessageiunknown.md) is encapsulating. 
  
```cpp
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



[IMAPISecureMessage : IUnknown](imapisecuremessageiunknown.md)
  
[IMessage : IMAPIProp](imessageimapiprop.md)

