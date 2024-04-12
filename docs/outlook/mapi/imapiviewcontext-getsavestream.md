---
title: "IMAPIViewContextGetSaveStream"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewContext.GetSaveStream
api_type:
- COM
ms.assetid: 8316bfa1-3077-401f-aa1e-e9492aca12a8
---

# IMAPIViewContext::GetSaveStream

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves a stream to be used for saving the current message.
  
```cpp
HRESULT GetSaveStream(
ULONG FAR * pulFlags,
ULONG FAR * pulFormat,
LPSTREAM FAR * ppstm
);
```

## Parameters

 _pulFlags_
  
> [out] Pointer to a bitmask of flags that controls how the message text should be saved. The following flag can be set:
    
MAPI_UNICODE 
  
> The message text is saved in Unicode format. If the MAPI_UNICODE flag is not set, the text is saved in ANSI format.
    
 _pulFormat_
  
> [out] Pointer to a bitmask of flags that controls the format of the saved text. The following flags can be set:
    
SAVE_FORMAT_RICHTEXT 
  
> The message text is to be saved as formatted text in the Rich Text Format (RTF). 
    
SAVE_FORMAT_TEXT 
  
> The message text is to be saved as plain text. 
    
 _ppstm_
  
> [out] Pointer to a pointer to the stream that will contain the saved message.
    
## Return value

S_OK 
  
> The stream was successfully retrieved.
    
## Remarks

Form objects call the **IMAPIViewContext::GetSaveStream** method to retrieve a stream an object that implements the **IStream** interface to support the handling of the Save As verb in the form viewer. The [IMAPIForm::DoVerb](imapiform-doverb.md) method, which is implemented in the form server and called by the form viewer to invoke a verb, should not return until the message is fully converted into the appropriate text format and placed into the appropriate stream. 
  
## Notes to callers

Do not write to the stream pointed to by  _ppstm_ before calling **GetSaveStream**. When **GetSaveStream** returns, do not reset the position of the seek pointer. This pointer must remain at the end of the saved message text. 
  
## See also



[IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md)

