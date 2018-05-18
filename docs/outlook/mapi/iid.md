---
title: "IID"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.IID
api_type:
- COM
ms.assetid: fa5498ab-2f8a-42f8-ba9d-1d555768594f
description: "Last modified: July 23, 2011"
---

# IID

  
  
**Applies to**: Outlook 
  
Describes a [GUID](guid.md) structure used to describe an identifier for a MAPI interface. 
  
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

See the **GUID** structure. 
  
## Remarks

An **IID** structure is used to uniquely identify a MAPI interface and to associate a particular interface with an object. For example, when a client calls [IMAPISession::OpenEntry](imapisession-openentry.md) to open a folder, the client sets the  _lpInterface_ parameter to point to an **IID** representing the [IMAPIFolder](imapifolderimapicontainer.md) interface. MAPI defines the **IMAPIFolderIID** to be IID_IMAPIFolder. **IID** structures are also used to uniquely identify OLE interfaces. 
  
All of the specific **IID** structures for the MAPI interfaces are defined in the Mapiguid.h header file. 
  
## See also



[GUID](guid.md)


[MAPI Structures](mapi-structures.md)

