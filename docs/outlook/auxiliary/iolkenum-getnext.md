---
title: "IOlkEnumGetNext"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: b387f896-c213-fc07-a12a-33917e620837
description: "Gets the next account in the enumerator."
 
 
---

# IOlkEnum::GetNext

Gets the next account in the enumerator.
  
## Quick Info

See [IOlkEnum](iolkenum.md).
  
```
HRESULT IOlkEnum:: GetNext( 
    LPUNKNOWN *ppunk 
);

```

## Parameters

 _ppunk_
  
> [in] A pointer to an **IUnknown** interface that the client can query to obtain an [IOlkAccount](iolkaccount.md) interface. 
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call succeeded.  <br/> |
|S_FALSE  <br/> |The enumerator has reached the end.  <br/> |
   
## Remarks

The interface specified by  *ppunk*  inherits from **IUnknown**. The client can query this interface (using **IUnknown::QueryInterface**) to obtain a pointer to an **IOlkAccount** interface, and get or set information for this account. 
  
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkEnum::GetCount](iolkenum-getcount.md)
  
[IOlkEnum::Reset](iolkenum-reset.md)
  
[IOlkEnum::Skip](iolkenum-skip.md)

