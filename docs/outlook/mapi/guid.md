---
title: "GUID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.GUID
api_type:
- COM
ms.assetid: e3608c47-06be-4476-a6ef-060fac252387
description: "Last modified: March 09, 2015"
---

# GUID

  
  
**Applies to**: Outlook 
  
Describes a globally unique identifier (GUID). 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiguid.h  <br/> |
   
```cpp
typedef struct _GUID
{
  unsigned long Data1;
  unsigned short Data2;
  unsigned short Data3;
  unsigned char Data4[8];
} GUID;

```

## Members

 **Data1**
  
> An unsigned long integer data value.
    
 **Data2**
  
> An unsigned short integer data value.
    
 **Data3**
  
> An unsigned short integer data value.
    
 **Data4**
  
> An array of unsigned characters.
    
## Remarks

 **GUID** structures are used in MAPI as follows: 
  
- In the [MAPIUID](mapiuid.md) structures that uniquely identify service providers. 
    
- For interface identifiers.
    
- In the property set names of named properties. 
    
Message store and address book providers generate a **GUID** structure to use in their **MAPIUID** structure. By passing the resulting **MAPIUID** to [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md), these service providers inform MAPI of their unique identifier.
  
Also, they are used in the implementation of Microsoft Remote Procedure Call (RPC) and the Object Description Language (ODL). For more information about these uses, see the  *Microsoft RPC Programmer's Guide and Reference*  ,  *OLE Programmer's Reference*  ,and  *Inside OLE*  ,  *Second Edition*  . 
  
The **GUID** structure is defined in the  *Win32 Programmer's Reference*  . Specific values for **GUID** structures that are used within MAPI are defined in the MAPI header file Mapiguid.h. 
  
## See also

#### Reference

[MAPIUID](mapiuid.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

