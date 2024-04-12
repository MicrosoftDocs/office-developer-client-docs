---
title: "ISocialPersonGetPicture"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 02fcaf25-42b5-4584-95c6-d44a3d035128
description: "Gets an array of bytes that contains the picture resource for the person."
---

# ISocialPerson::GetPicture

Gets an array of bytes that contains the picture resource for the person. 
  
```cpp
HRESULT _stdcall GetPicture([out, retval] SAFEARRAY(unsigned char)* picture);
```

## Parameters

_picture_
  
> [out] A pointer to a structure that specifies an array of bytes that represent the picture resource for a person.
    
## Remarks

Supported picture resources are in .bmp, .jpeg, or .png format.
  
## See also

- [ISocialPerson : IUnknown](isocialpersoniunknown.md)

