---
title: "SMAPIFormProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SMAPIFormProp
api_type:
- COM
ms.assetid: 80f1c2e0-3567-4b16-86cb-d5e6ac95c2ee
description: "Last modified: March 09, 2015"
---

# SMAPIFormProp

  
  
**Applies to**: Outlook 
  
Describes a named property used with a form. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
   
```cpp
typedef struct _SMAPIFormProp
{
  ULONG ulFlags;
  ULONG nPropType;
  MAPINAMEID nmid;
  LPSTR pszDisplayName;
  FORMPROPSPECIALTYPE nSpecialType;
  union
  {
    struct
    {
      MAPINAMEID nmidIdx;
      ULONG cfpevAvailable;
      LPMAPIFORMPROPENUMVAL pfpevAvailable;
    } s1;
  } u;
} SMAPIFormProp, FAR * LPMAPIFORMPROP;

```

## Members

 **ulFlags**
  
> Flags used to distinguish the format of the strings in the **SMAPIFormProp** structure. The following flag can be set: 
    
MAPI_UNICODE 
  
> The strings returned are in Unicode format. If MAPI_UNICODE is not set, the strings are in ANSI format.
    
 **nPropType**
  
> Type of the named property, with the most significant word set to zero. 
    
 **nmid**
  
> Name for the named property, which includes a **GUID** structure identifying the property set and either a numeric or string value that represents an interface identifier and form name. 
    
 **pszDisplayName**
  
> Pointer to the display name of the named property.
    
 **nSpecialType**
  
> Value describing the type of data included in the **u** member. Possible values are as follows: 
    
FPST_VANILLA 
  
> The **u** member does not contain an enumeration. 
    
FPST_ENUM_PROP 
  
> The **u** member contains a structure that describes an enumeration. 
    
 **u**
  
> Union describing the association between the name and number of the named property. By using some properties, the **u** member is empty. With other properties, it is represented in a structure consisting of the following members: 
    
 **nmidIdx**
  
> The [MAPINAMEID](mapinameid.md) structure that contains the property set and identifier for the named property. 
    
 **cfpevAvailable**
  
> Count of [SMAPIFormPropEnumVal](smapiformpropenumval.md) structures in the array pointed to by the **pfpevAvailable** member. 
    
 **pfpevAvailable**
  
> Pointer to an array of **SMAPIFormPropEnumVal** structures, each of which holds a value for the named property. 
    
## Remarks

The **SMAPIFormProp** structure contains information about a form property used as part of the definitions of the [IMAPIFormInfo](imapiforminfoimapiprop.md) interface; **nSpecialType** contains a tag that applies to the **u** union that is part of **SMAPIFormProp**.
  
## See also

#### Reference

[MAPINAMEID](mapinameid.md)
  
[SMAPIFormPropEnumVal](smapiformpropenumval.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

