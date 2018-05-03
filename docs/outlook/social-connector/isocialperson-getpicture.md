---
title: "ISocialPersonGetPicture"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 02fcaf25-42b5-4584-95c6-d44a3d035128
description: "Gets an array of bytes that contains the picture resource for the person."
---

# ISocialPerson::GetPicture

Gets an array of bytes that contains the picture resource for the person. 
  
```
HRESULT _stdcall GetPicture([out, retval] SAFEARRAY(unsigned char)* picture);
```

## Parameters

 _picture_
  
> [out] A pointer to a structure that specifies an array of bytes that represent the picture resource for a person.
    
## Remarks

Supported picture resources are in .bmp, .jpeg, or .png format.
  
## See also

#### Reference

[ISocialPerson : IUnknown](isocialpersoniunknown.md)

