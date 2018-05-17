---
title: "IPropDataHrGetPropAccess"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPropData.HrGetPropAccess
api_type:
- COM
ms.assetid: 0101d291-00ca-4f66-b857-75d74b9f91a1
description: "Last modified: March 09, 2015"
---

# IPropData::HrGetPropAccess

  
  
**Applies to**: Outlook 
  
Retrieves the access level and status for one or more of the object's properties.
  
```
HRESULT HrGetPropAccess(
  LPSPropTagArray FAR * lppPropTagArray,
  ULONG FAR * FAR * lprgulAccess
);
```

## Parameters

 _lppPropTagArray_
  
> [in, out] On input, an array of property tags that indicate the properties for which to retrieve access levels and status; otherwise, a pointer to NULL, which indicates that **HrGetPropAccess** should retrieve access levels and status for all properties. On output, an array of property tags for which access and status flags were retrieved. The flags are stored in the array pointed to by the  _lprgulAccess_ parameter. 
    
 _lprgulAccess_
  
> [out] A pointer to an array of flag bitmasks. Each bitmask indicates the access levels or status, or both, for each of the properties identified in the array pointed to by the  _lpPropTagArray_ parameter. The two arrays are positional in that the first bitmask that  _lprgulAccess_ points to describes the first property that  _lpPropTagArray_ points to, and so on. For each property tag, the following flags can be set: 
    
|**Access-level flag**|**Status flag**|
|:-----|:-----|
|IPROP_READONLY, which indicates that the property cannot be modified.  <br/> |IPROP_CLEAN, which indicates that the property has not been modified.  <br/> |
|IPROP_READWRITE, which indicates that the property can be modified.  <br/> |IPROP_DIRTY, which indicates that the property has been modified.  <br/> |
   
## Return value

S_OK 
  
> The access level and status flags for the properties were successfully returned.
    
## Remarks

The **IPropData::HrGetPropAccess** method retrieves a set of flags that indicates the access level and status for one or more properties. 
  
## Notes to Callers:

You can use **HrGetPropAccess** for the following purposes: 
  
- To determine whether a client changed or deleted a writable property.
    
- To prevent a client from changing or deleting a property by using the [IMAPIProp](imapipropiunknown.md) methods. 
    
If one of the properties in the property tag array pointed to by  _lppPropTagArray_ has been deleted, **HrGetPropAccess** sets the array entry to 0 on output. If you set  _lppPropTagArray_ to NULL and one of the object's properties has been deleted, the deleted property is returned in the array. 
  
If a property has been modified, its IPROP_DIRTY flag is set in the corresponding entry in the array that  _lprgulAccess_ points to. Neither IPROP_READONLY nor IPROP_READWRITE will be set. 
  
If a property has not been modified or deleted, only the IPROP_READONLY or IPROP_READWRITE flag will be set. 
  
## See also

#### Reference

[SPropTagArray](sproptagarray.md)
  
[IPropData : IMAPIProp](ipropdataimapiprop.md)

