---
title: "IMAPIFormInfoMakeIconFromBinary"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormInfo.MakeIconFromBinary
api_type:
- COM
ms.assetid: 4daeddd7-3f0c-4178-ae8d-f74814090d40
description: "Last modified: July 23, 2011"
---

# IMAPIFormInfo::MakeIconFromBinary

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Builds an icon from one of the icon properties of a form.
  
```
HRESULT MakeIconFromBinary(
  ULONG nPropID,
  HICON FAR * phicon
);
```

## Parameters

 _nPropID_
  
> [in] A property identifier for an icon property.
    
 _phicon_
  
> [out] A pointer to the returned icon.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Client applications call the **IMAPIFormInfo::MakeIconFromBinary** method to build an icon from one of the icon properties of a form. In the  _nPropID_ parameter, **MakeIconFromBinary** takes the property identifier of one of the icon properties of a form. Using this property identifier, it builds an icon that can be displayed in table views that include property columns for icons. 
  
## See also

#### Reference

[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)

