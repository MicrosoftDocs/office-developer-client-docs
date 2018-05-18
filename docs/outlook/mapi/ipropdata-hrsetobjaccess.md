---
title: "IPropDataHrSetObjAccess"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPropData.HrSetObjAccess
api_type:
- COM
ms.assetid: 01bd3235-22cc-4ff3-b2b6-341ce622128b
description: "Last modified: July 23, 2011"
---

# IPropData::HrSetObjAccess

  
  
**Applies to**: Outlook 
  
Sets the access level for the object.
  
```cpp
HRESULT HrSetObjAccess(
  ULONG ulAccess
);
```

## Parameters

 _ulAccess_
  
> [in] A bitmask of flags that specifies the object's access level. One of the following flags can be set:
    
IPROP_READONLY 
  
> Sets the object's access level to read-only. 
    
IPROP_READWRITE 
  
> Sets the object's access level to read/write.
    
## Return value

S_OK 
  
> The object's access level was successfully set.
    
## Remarks

The **IPropData::HrSetObjAccess** method sets the access level for an entire object, rather than for individual properties. **HrSetObjAccess** can be used to change the access level established when the object was created. 
  
## Notes to callers

To set an access level on a property, first call **HrSetObjAccess** with the IPROP_READWRITE flag set in the  _ulAccess_ parameter to make the object modifiable. Then call the [IPropData::HrSetPropAccess](ipropdata-hrsetpropaccess.md) method, specifying the target property in the array pointed to by the  _lpPropTagArray_ parameter. 
  
To create an object with properties that will be read-only to clients, create a read/write object, add the necessary properties, and then call **HrSetObjAccess** to change the object's access to read-only. 
  
You can also use **HrSetObjAccess** to prevent clients from creating new properties. 
  
## See also



[IPropData::HrGetPropAccess](ipropdata-hrgetpropaccess.md)
  
[IPropData::HrSetPropAccess](ipropdata-hrsetpropaccess.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)

