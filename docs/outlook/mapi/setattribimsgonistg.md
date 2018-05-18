---
title: "SetAttribIMsgOnIStg"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SetAttribIMsgOnIStg
api_type:
- COM
ms.assetid: 683d0d00-1b93-445d-86ff-180a3e6d2323
description: "Last modified: March 09, 2015"
---

# SetAttribIMsgOnIStg

  
  
**Applies to**: Outlook 
  
Sets or alters attributes of properties on an [IMessage](imessageimapiprop.md) object supplied by the [OpenIMsgOnIStg](openimsgonistg.md) function. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and message store providers  <br/> |
   
```cpp
HRESULT SetAttribIMsgOnIStg(
  LPVOID lpObject,
  LPSPropTagArray lpPropTags,
  LPSPropAttrArray lpPropAttrs,
  LPSPropProblemArray FAR * lppPropProblems
);
```

## Parameters

 _lpObject_
  
> [in] Pointer to the object for which property attributes are being set. 
    
 _lpPropTags_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure containing an array of property tags indicating the properties for which property attributes are being set. 
    
 _lpPropAttrs_
  
> [in] Pointer to an [SPropAttrArray](spropattrarray.md) structure listing the property attributes to set. 
    
 _lppPropProblems_
  
> [out] Pointer to the returned [SPropProblemArray](spropproblemarray.md) structure containing a set of property problems. This structure identifies problems encountered if **SetAttribIMsgOnIStg** has been able to set some properties, but not all. If a pointer to NULL is passed in the  _lppPropProblems_ parameter, no property problem array is returned even if some properties were not set. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded overall, but one or more properties could not be accessed and were returned with a property type of PT_ERROR.
    
## Remarks

Property attributes can only be accessed on property objects, that is, objects implementing the [IMAPIProp : IUnknown](imapipropiunknown.md) interface. To make MAPI properties available on an OLE structured storage object, [OpenIMsgOnIStg](openimsgonistg.md) builds an [IMessage : IMAPIProp](imessageimapiprop.md) object on top of the OLE **IStorage** object. The property attributes on such objects can be set or altered with **SetAttribIMsgOnIStg** and retrieved with [GetAttribIMsgOnIStg](getattribimsgonistg.md). 
  
 **Note** **GetAttribIMsgOnIStg** and **SetAttribIMsgOnIStg** do not operate on all **IMessage** objects. They are only valid for **IMessage**-on- **IStorage** objects returned by **OpenIMsgOnIStg**. 
  
In the  _lpPropAttrs_ parameter, the number and position of the attributes must match the number and position of the property tags passed in the  _lpPropTags_ parameter. 
  
The **SetAttribIMsgOnIStg** function is used to make message properties read-only when required by the **IMessage** schema. The sample message store provider uses it for this purpose. For more information, see [Messages](mapi-messages.md). 
  

