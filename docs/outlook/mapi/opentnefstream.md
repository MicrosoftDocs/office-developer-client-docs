---
title: "OpenTnefStream"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.OpenTnefStream
api_type:
- COM
ms.assetid: 912d7799-53ce-42a7-9fbd-f9a6a3a56047
description: "Last modified: March 09, 2015"
---

# OpenTnefStream

**Applies to**: Outlook 2013 | Outlook 2016 
  
Called by a transport provider to initiate a MAPI Transport Neutral Encapsulation Format (TNEF) session. 
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Tnef.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Transport providers  <br/> |
   
```cpp
HRESULT OpenTnefStream(
  LPVOID lpvSupport,
  LPSTREAM lpStream,
  LPSTR lpszStreamName, 
  ULONG ulFlags,
  LPMESSAGE lpMessage,
  WORD wKey,
  LPITNEF FAR * lppTNEF
);
```

## Parameters

_lpvSupport_
  
> [in] Passes a support object, or passes in NULL. 
    
_lpStream_
  
> [in] Pointer to a storage stream object OLE **IStream** interface providing a source or destination for a TNEF stream message. 
    
_lpszStreamName_
  
> [in] Pointer to the name of the data stream that the TNEF object uses. If the caller has set the TNEF_ENCODE flag ( _ulFlags_ parameter) in its call to **OpenTnefStream**, the  _lpszName_ parameter must specify a non-null pointer to a non-null string consisting of any characters considered valid for naming a file. MAPI does not allow string names including the characters "[", "]", or ":", even if the file system permits their use. The size of the string passed for  _lpszName_ must not exceed the value of MAX_PATH, the maximum length of a string that contains a path name. 
    
_ulFlags_
  
> [in] Bitmask of flags used to indicate the mode of the function. The following flags can be set:
    
TNEF_BEST_DATA 
  
> All possible properties are mapped into their down-level attributes, but when there is a possible data loss due to the conversion to a down-level attribute, the property is also encoded in the encapsulations. Note that this will cause the duplication of information in the TNEF stream. TNEF_BEST_DATA is the default if no other modes are specified. 
    
TNEF_COMPATIBILITY 
  
> Provides backward compatibility with the older client applications. TNEF streams encoded with this flag will map all possible properties into their corresponding down-level attribute. This mode also causes the defaulting of some properties that are required by down-level clients. 
    
  > [!CAUTION]
  > This flag is obsolete and should not be used. 
  
TNEF_DECODE 
  
> The TNEF object on the indicated stream is opened with read-only access. The transport provider must set this flag if it wants the function to initialize the object for subsequent decoding.
    
TNEF_ENCODE 
  
> The TNEF object on the indicated stream is opened for read/write permission. The transport provider must set this flag if it wants the function to initialize the object for subsequent encoding.
    
TNEF_PURE 
  
> Encodes all properties into the MAPI encapsulation blocks. Therefore, a "pure" TNEF file will consist of, at most, attMAPIProps, attAttachment, attRenddata, and attRecipTable. This mode is ideal for use when no backward compatibility is required.
    
_lpMessage_
  
> [in] Pointer to a message object as a destination for a decoded message with attachments or a source for an encoded message with attachments. Any properties of a destination message might be overwritten by the properties of an encoded message.
    
_wKey_
  
> [in] A search key that the TNEF object uses to match attachments to the text tags inserted in the message text. This value should be relatively unique across messages.
    
_lppTNEF_
  
> [out] Pointer to the new TNEF object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

A TNEF object created by the **OpenTnefStream** function later calls the OLE method **IUnknown::AddRef** to add references for the support object, the stream object, and the message object. The transport provider can release the references for all three objects with a single call to the OLE method **IUnknown::Release** on the TNEF object. 
  
**OpenTnefStream** allocates and initializes a TNEF object **ITnef** interface for the provider to use in encoding a MAPI message **IMessage** interface into a TNEF stream message. Alternatively, the function can set up the object for the provider to use in subsequent calls to [ITnef::ExtractProps](itnef-extractprops.md) to decode a TNEF stream message into a MAPI message. To free the TNEF object and close the session, the transport provider must call the inherited **IUnknown::Release** method on the object. 
  
This function is the original entry point for TNEF access and has been replaced by [OpenTnefStreamEx](opentnefstreamex.md) but is still used for compatibility for those already using TNEF. 
  
## See also

- [IMAPISupport : IUnknown](imapisupportiunknown.md)
- [IXPProvider::TransportLogon](ixpprovider-transportlogon.md)

