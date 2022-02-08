---
title: "IPropDataHrSetPropAccess"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IPropData.HrSetPropAccess
api_type:
- COM
ms.assetid: 02365050-5e8b-437c-925f-4eb0df646356
description: "Last modified: March 09, 2015"
---

# IPropData::HrSetPropAccess

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the access level or status for one or more of the object's properties.
  
```cpp
HRESULT HrSetPropAccess(
  LPSPropTagArray lpPropTagArray,
  ULONG FAR * rgulAccess
);
```

## Parameters

 _lpPropTagArray_
  
> [in] A pointer to an array of property tags that indicate the properties to be modified. 
    
 _rgulAccess_
  
> [in] An array of flag bitmasks. Each bitmask indicates the access levels or status, or both, for each of the properties identified in the array that the  _lpPropTagArray_ parameter points to. The two arrays are positional in that the first bitmask in  _rgulAccess_ describes the first property that  _lpPropTagArray_ points to, and so on. For each property tag, one access-level flag and one status flag can be set. The following table shows the possible flags. 
    
|**Access-level flag**|**Status flag**|
|:-----|:-----|
|IPROP_READONLY, which indicates that the property cannot be modified  <br/> |IPROP_CLEAN, which indicates that the property has not been modified.  <br/> |
|IPROP_READWRITE, which indicates that the property can be modified.  <br/> |IPROP_DIRTY, which indicates that the property has been modified.  <br/> |
   
## Return value

S_OK 
  
> The access-level and status flags have been successfully set.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to set a property on a read-only object or an object for which the caller has insufficient permissions.
    
MAPI_E_INVALID_PARAMETER 
  
> The  _rgulAccess_ parameter contains an invalid combination of flags, such as IPROP_READONLY and IPROP_READWRITE. 
    
## Remarks

The **IPropData::HrSetPropAccess** method changes the access level and status for the properties that are identified by the property tags in the [SPropTagArray](sproptagarray.md) structure pointed to by the  _lpPropTagArray_ parameter. For each property, there is a corresponding entry in the _rgulAccess_ array. The entry can be set to one flag that indicates the property's access level and another flag that indicates its status. 
  
## Notes to callers

Use **HrSetPropAccess** to determine when a particular property value changes and to change the access level for one or more of an object's properties. 
  
## See also



[SPropTagArray](sproptagarray.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)

