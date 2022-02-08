---
title: "GetAttribIMsgOnIStg"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.GetAttribIMsgOnIStg
api_type:
- COM
ms.assetid: bb27b28a-b2bd-4d4a-b0bb-0692f3de8e16
description: "Last modified: March 09, 2015"
---

# GetAttribIMsgOnIStg

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Retrieves attributes of properties on an [IMessage](imessageimapiprop.md) object supplied by the [OpenIMsgOnIStg](openimsgonistg.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and message store providers  <br/> |
   
```cpp
HRESULT GetAttribIMsgOnIStg(
  LPVOID lpObject,
  LPSPropTagArray lpPropTagArray,
  LPSPropAttrArray FAR * lppPropAttrArray
);
```

## Parameters

 _lpObject_
  
> [in] Pointer to an **IMessage** object obtained from the [OpenIMsgOnIStg](openimsgonistg.md) function. 
    
 _lpPropTagArray_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags indicating the properties for which attributes are to be retrieved. 
    
 _lppPropAttrArray_
  
> [out] Pointer to a pointer to the returned [SPropAttrArray](spropattrarray.md) structure that contains the retrieved property attributes. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded overall, but one or more properties could not be accessed and were returned with a property type of PT_ERROR.
    
## Remarks

Property attributes can only be accessed on property objects, that is, objects implementing the [IMAPIProp : IUnknown](imapipropiunknown.md) interface. To make MAPI properties available on an OLE structured storage object, [OpenIMsgOnIStg](openimsgonistg.md) builds an [IMessage : IMAPIProp](imessageimapiprop.md) object on top of the OLE **IStorage** object. The property attributes on such objects can be set or altered with [SetAttribIMsgOnIStg](setattribimsgonistg.md) and retrieved with **GetAttribIMsgOnIStg**. 
  
> [!NOTE]
> **GetAttribIMsgOnIStg** and **SetAttribIMsgOnIStg** do not operate on all **IMessage** objects. They are only valid for **IMessage**-on- **IStorage** objects returned by **OpenIMsgOnIStg**. 
  
The number and positions of the attributes in the _lppPropAttrArray_ parameter correspond to the number and positions of the property tags in the _lpPropTagArray_ parameter. 
  

