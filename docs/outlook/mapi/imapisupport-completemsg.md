---
title: "IMAPISupportCompleteMsg"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.CompleteMsg
api_type:
- COM
ms.assetid: e7932433-abe0-4341-95e0-91b37c848145
---

# IMAPISupport::CompleteMsg

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Performs postprocessing on a message. 
  
```cpp
HRESULT CompleteMsg(
  ULONG ulFlags,
  ULONG cbEntryID,
  LPENTRYID lpEntryID
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _cbEntryID_
  
> [in] The byte count in the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier of the message to process.
    
## Return value

S_OK 
  
> The postprocessing was successful.
    
## Remarks

The **IMAPISupport::CompleteMsg** method is implemented for message store provider support objects and is called only by message store providers that are tightly coupled with transport providers. Tightly coupled store providers call **IMAPISupport::CompleteMsg** to instruct the MAPI spooler to postprocess a message. 
  
## Notes to callers

Call **CompleteMsg** only when you are tightly coupled with a transport provider, you can handle all of the message's recipients, and one of the following conditions exists: 
  
- The message was preprocessed.
    
- The message requires postprocessing by the MAPI spooler.
    
## See also



[IMAPISupport : IUnknown](imapisupportiunknown.md)

