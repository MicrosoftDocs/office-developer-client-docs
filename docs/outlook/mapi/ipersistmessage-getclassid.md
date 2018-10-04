---
title: "IPersistMessageGetClassID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPersistMessage.GetClassID
api_type:
- COM
ms.assetid: 77eeb468-3432-4ccd-9c1e-1df9ce605193
description: "Last modified: July 23, 2011"
---

# IPersistMessage::GetClassID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns an identifier that represents the form server that can manage the form. 
  
```cpp
HRESULT GetClassID(
  LPCLSID lpClassID
);
```

## Parameters

 _lpClassID_
  
> [in, out] A pointer to the class identifier (CLSID) of the form.
    
## Return value

S_OK 
  
> The class identifier was successfully returned.
    
## Remarks

The **IPersistMessge::GetClassID** method sets the contents of the  _lpClassID_ parameter to the form server's class identifier and returns S_OK. When a form viewer calls **GetClassID** and it returns successfully, the form is placed in the [Uninitialized](uninitialized-state.md) state. 
  
For more information about how class identifiers are used with structured storage objects, see the documentation for the [IPersist::GetClassID](https://msdn.microsoft.com/library/921a3b86-a240-454e-9411-8d653e02b90e.aspx) method. 
  
## See also



[IPersistMessage : IUnknown](ipersistmessageiunknown.md)

