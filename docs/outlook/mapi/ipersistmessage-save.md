---
title: "IPersistMessageSave"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.Save
api_type:
- COM
ms.assetid: 17875c13-f55b-4538-ac6f-c020281c3175
description: "Last modified: July 23, 2011"
---

# IPersistMessage::Save

  
  
**Applies to**: Outlook 
  
Saves a revised form back to the message from which it was loaded or created.
  
```cpp
HRESULT Save(
  LPMESSAGE pMessage,
  ULONG fSameAsLoad
);
```

## Parameters

 _pMessage_
  
> [in] A pointer to the message.
    
 _fSameAsLoad_
  
> [in] TRUE to indicate that the message pointed to by  _pMessage_ is the message from which the form was loaded or created; otherwise, FALSE. 
    
## Return value

S_OK 
  
> The form was successfully saved.
    
## Remarks

Form viewers call the **IPersistMessage::Save** method to save a revised form back to the message from which it was loaded or created. 
  
 **Save** should only be called when the form is in its [Normal](normal-state.md) state. 
  
## Notes to Implementers

Do not commit the saved changes; it is up to the caller to commit the changes. Never make changes to the properties that belong to the form's message except during the **Save** call. 
  
If  _fSameAsLoad_ is set to TRUE, you can save the changes to the form's existing message. If  _fSameAsLoad_ is set to FALSE, you must copy all of the properties from the original message into the message pointed to by  _pMessage_ before performing the save. Use the original message's [IMAPIProp::CopyTo](imapiprop-copyto.md) method to copy the properties. 
  
When all of the properties have been copied, enter the [NoScribble](noscribble-state.md) state. If no errors occur, return S_OK. Otherwise, return the error from the failed action. 
  
If **Save** is called when the form is in any state other than Normal, return E_UNEXPECTED. 
  
For more information about saving storage objects, see the documentation on the [IPersistStorage](http://msdn.microsoft.com/library/1c1a20fc-c101-4cbc-a7a6-30613aa387d7%28Office.15%29.aspx) methods. 
  
## See also

#### Reference

[IPersistMessage : IUnknown](ipersistmessageiunknown.md)
#### Concepts

[Form States](form-states.md)

