---
title: "IMAPISupportExpandRecips"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.ExpandRecips
api_type:
- COM
ms.assetid: 78edd549-d557-489a-85f5-adfb5c44a7d4
---

# IMAPISupport::ExpandRecips

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Completes a message's recipient list, expanding particular distribution lists.
  
```cpp
HRESULT ExpandRecips(
  LPMESSAGE lpMessage,
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpMessage_
  
> [in] A pointer to the message that has the recipient list to be processed.
    
 _lpulFlags_
  
> [out] A pointer to a bitmask of flags that controls the type of processing that occurs. The following flags can be set:
    
NEEDS_PREPROCESSING 
  
> The message needs to be preprocessed before it is sent.
    
NEEDS_SPOOLER 
  
> The MAPI spooler (rather than the transport provider to which the caller is tightly coupled) must send the message.
    
## Return value

S_OK 
  
> The message's recipient list was successfully processed.
    
## Remarks

The **IMAPISupport::ExpandRecips** method is implemented for message store provider support objects. Message store providers call **ExpandRecips** to prompt MAPI to perform the following tasks: 
  
- Expand certain personal distribution lists to their component recipients.
    
- Replace all display names that have been changed with the original names.
    
- Mark any duplicate entries.
    
- Resolve all one-off addresses. 
    
- Check whether the message needs preprocessing and, if it does, set the flag pointed to by  _lpulFlags_ to NEEDS_PREPROCESSING. 
    
 **ExpandRecips** expands any distribution lists that have the messaging address type of MAPIPDL. 
  
## Notes to callers

Always call **ExpandRecips** as part of your message processing. Make a call to **ExpandRecips** one of the first calls in your [IMessage::SubmitMessage](imessage-submitmessage.md) method implementation. 
  
## See also



[IMessage::SubmitMessage](imessage-submitmessage.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

