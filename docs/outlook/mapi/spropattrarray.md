---
title: "SPropAttrArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SPropAttrArray
api_type:
- COM
ms.assetid: 30dd19d9-0840-49e9-aec6-ec8d19b1f91d
description: "Last modified: March 09, 2015"
---

# SPropAttrArray

  
  
**Applies to**: Outlook 
  
Contains a list of attributes for properties of an object. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Imessage.h  <br/> |
|Related macros:  <br/> |[CbNewSPropAttrArray](cbnewspropattrarray.md), [CbSPropAttrArray](cbspropattrarray.md) <br/> |
   
```
typedef struct
{
  ULONG cValues;
  ULONG aPropAttr[MAPI_DIM];
} SPropAttrArray, FAR *LPSPropAttrArray;

```

## Members

 **cValues**
  
> Count of property attributes in the **aPropAttr** member. 
    
 **aPropAttr**
  
> An array of property attributes. Valid values for attributes are as follows:
    
    - PROPATTR_MANDATORY
    
    - PROPATTR_READABLE
    
    - PROPATTR_WRITEABLE
    
    - PROPATTR_NOT_PRESENT
    
## Remarks

The **SPropAttrArray** structure is used by property data objects that implement the [IPropData : IMAPIProp](ipropdataimapiprop.md) interface. It is also used by MAPI's implementation of [IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md) that is based on structured storage. 
  
## See also

#### Reference

[IPropData : IMAPIProp](ipropdataimapiprop.md)
  
[IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md)
  
[CbNewSPropAttrArray](cbnewspropattrarray.md)
  
[CbSPropAttrArray](cbspropattrarray.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

