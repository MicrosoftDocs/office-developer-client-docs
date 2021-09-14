---
title: "GetTnefStreamCodepage"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 0f22ccf2-1004-4731-9d68-f66c01b4588b
description: "Last modified: March 09, 2015"
---

# GetTnefStreamCodepage

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines the code page for a Transport-Neutral Encapsulation Format (TNEF) stream.
  
|||
|:-----|:-----|
|Header file:  <br/> |tnef.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers.  <br/> |
   
```cpp
HRESULT GetTnefStreamCodepage(
  LPSTREAM lpStream,
  ULONG FAR * lpulCodepage,
  ULONG FAR * lpulSubCodepage
);
```

## Parameters

 _lpStream_
  
> [in] Pointer to a storage stream object OLE **IStream** interface providing a source for a TNEF stream message. 
    
 _lpulCodepage_
  
> [out] Pointer to the code page of the stream.
    
 _lpulSubCodepage_
  
> [out] Pointer to the subcode page of the stream.
    
## Return value

 **S_OK**
  
> The call succeeded and has returned the expected value or values.
    
 **MAPI_E_NOT_ENOUGH_DISK**
  
> There was an error reading an attribute in the TNEF stream.
    
 **MAPI_E_CORRUPT_DATA**
  
> Either the stream was not a TNEF stream or there was an error reading the attOemCodepage attribute.
    
## Remarks

Use the **GetTnefStreamCodepage** function to read the **attOemCodepage** attribute of the TNEF stream to determine the code page and subcode page. If **attOemCodepage** is not found, **GetTnefStreamCodepage** returns a code page of 437 and a subcode page of 0. 
  
## See also



[attOemCodepage](https://msdn.microsoft.com/library/ee158667%28EXCHG.80%29.aspx)

