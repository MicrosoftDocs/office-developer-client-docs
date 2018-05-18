---
title: "ITnefOpenTaggedBody"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITnef.OpenTaggedBody
api_type:
- COM
ms.assetid: 70d5b34c-85b3-4d1f-860e-2838947ba428
description: "Last modified: July 23, 2011"
---

# ITnef::OpenTaggedBody

  
  
**Applies to**: Outlook 
  
Opens a stream interface on the text of an encapsulated message.
  
```cpp
HRESULT OpenTaggedBody(
  LPMESSAGE lpMessage,
  ULONG ulFlags,
  LPSTREAM FAR * lppStream
);
```

## Parameters

 _lpMessage_
  
> [in] A pointer to the message with which the stream is associated. This message is not required to be the same message that is passed in the call to the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the stream interface is opened. The following flags can be set:
    
MAPI_CREATE 
  
> If a property does not exist in the current message, it should be created. If the property does exist, the current data in the property should be replaced with the data from the Transport-Neutral Encapsulation Format (TNEF) stream. When an implementation sets the MAPI_CREATE flag, it should also set the MAPI_MODIFY flag.
    
MAPI_MODIFY 
  
> Requests read/write permission. The default interface is read-only. MAPI_MODIFY must be set whenever MAPI_CREATE is set.
    
 _lppStream_
  
> [out] A pointer to a pointer to a stream object that contains the text from the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property of the passed-in encapsulated message and that supports the [IStream](http://msdn.microsoft.com/library/stg.istream%28Office.15%29.aspx) interface. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::OpenTaggedBody** method to open a stream interface on the text of an encapsulated message (that is, on a TNEF object). 
  
As part of its processing, **OpenTaggedBody** either inserts or parses attachment tags that indicate the position of any attachments or OLE objects in the message text. The attachment tags are in the following format: 
  
 **[[** _attachment name_ **:** _n_ **in** _attachment container name_ **]]**
  
 _attachment name_ describes the attachment object;  _n_ is a number that identifies the attachment that is part of a sequence, incrementing from the value passed in the  _lpKey_ parameter of the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function; and  _attachment container name_ describes the physical component where the attachment object resides. 
  
 **OpenTaggedBody** reads out message text and inserts an attachment tag wherever an attachment object originally appeared in the text. The original message text is not changed. 
  
When a message that has tags is passed to a stream, the tags are stripped out and the attachment objects are relocated in the position of the tags in the stream.
  
## See also



[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[PidTagBody Canonical Property](pidtagbody-canonical-property.md)
  
[ITnef : IUnknown](itnefiunknown.md)

