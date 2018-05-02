---
title: "IPersistMessageHandsOffMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.HandsOffMessage
api_type:
- COM
ms.assetid: 0e56b21d-0a2e-4fe6-83f4-c9daab2f3055
description: "Last modified: July 23, 2011"
---

# IPersistMessage::HandsOffMessage

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Causes the form to release its current message.
  
```
HRESULT HandsOffMessage( void );
```

## Parameters

None
  
## Return value

S_OK 
  
> The message was successfully released.
    
## Remarks

Forms transition into two HandsOff states:
  
- [HandsOffAfterSave](handsoffaftersave-state.md)
    
- [HandsOffFromNormal](handsofffromnormal-state.md)
    
When a form is in either of these states, it is in the process of being stored permanently. 
  
## Notes to Implementers

When a form viewer calls the **IPersistMessage::HandsOffMessage** method while your form is in the [Normal](normal-state.md) or [NoScribble](noscribble-state.md) state, recursively call **HandsOffMessage** on each message embedded in the current message and the [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/1e5ef26f-d8e7-4fa6-bfc4-19dace35314d.aspx) method on each OLE object embedded in the current message. Then release the current message and all embedded messages and OLE objects. If your form was in the Normal state, transition to the HandsOffFromNormal state. If your form was in the NoScribble state, transition to the HandsOffAfterSave state. After a successful transition, call the message's [IUnknown::Release](http://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method and return S_OK. 
  
When a form viewer calls **HandsOffMessage** while your form is in either of the HandsOff states, return E_UNEXPECTED. 
  
For more information about the different states of a form, see [Form States](form-states.md). For more information about how to work with the HandsOff state of storage objects, see the [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/1e5ef26f-d8e7-4fa6-bfc4-19dace35314d.aspx) method. 
  
## See also

#### Reference

[IPersistMessage : IUnknown](ipersistmessageiunknown.md)
#### Concepts

[Form States](form-states.md)

