---
title: "MAPINAMEID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.MAPINAMEID
api_type:
- COM
ms.assetid: 9a92e9cd-8282-4cf0-93af-4089b3763594
description: "Describes a named property. Named properties enable clients to define custom properties in a larger namespace than the MAPI-defined property identifier range."
---

# MAPINAMEID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a named property. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _MAPINAMEID
{
  LPGUID lpguid;
  ULONG ulKind;
  union
  {
    LONG lID;
    LPWSTR lpwstrName;
  } Kind;
} MAPINAMEID, FAR *LPMAPINAMEID;

```

## Members

 **lpguid**
  
> Pointer to a [GUID](guid.md) structure defining a particular property set; this member cannot be NULL. Valid values are as follows: 
    
PS_PUBLIC_STRINGS
  
> 
    
PS_MAPI
  
> 
    
A client-defined value
  
> 
    
 **ulKind**
  
> Value describing the type of value in the **Kind** member. Valid values are as follows: 
    
MNID_ID 
  
> The **Kind** member contains an integer value that represents the property name. 
    
MNID_STRING 
  
> The **Kind** member contains a Unicode character string representing the property name. 
    
 **Kind**
  
> Union describing the name of the named property. The name can be either an integer value, stored in **lID**, or a Unicode character string, stored in **lpwstrName**.
    
## Remarks

The **MAPINAMEID** structure is used to describe named properties properties that have identifiers over 0x8000. A property set is an important part a named property. For example PS_PUBLIC_STRINGS or PS_ROUTING_ADDRTYPE are property sets defined by MAPI. 
  
Named properties enable clients to define custom properties in a larger namespace than is available in the MAPI-defined property identifier range. Property names cannot be used to obtain property values directly; they must first be mapped to property identifiers through the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) method. For particular objects such as messages, MAPI reserves a range of property identifiers for custom properties. Therefore, for these objects, clients do not have to use named properties and can save the associated overhead. 
  
For more information about named properties, see [Named Properties](mapi-named-properties.md).
  
## See also



[GUID](guid.md)
  
[IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md)


[MAPI Structures](mapi-structures.md)

