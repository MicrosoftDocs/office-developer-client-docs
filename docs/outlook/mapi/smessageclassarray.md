---
title: "SMessageClassArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SMessageClassArray
api_type:
- COM
ms.assetid: 05f8c191-db2b-4174-8b3c-a9fdabfe6ac8
description: "Last modified: March 09, 2015"
---

# SMessageClassArray

  
  
**Applies to**: Outlook 
  
Contains an array of pointers to message class strings.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Related macro:  <br/> |[CbMessageClassArray](cbmessageclassarray.md) <br/> |
   
```
typedef struct 
{
  ULONG cValues;
  LPCSTR aMessageClass[MAPI_DIM];
} SMessageClassArray, FAR * LPSMESSAGECLASSARRAY;

```

## Members

 **cValues**
  
> Count of message class string pointers in the array.
    
 **aMessageClass**
  
> Array of pointers to message class strings.
    
## Remarks

The **SMessageClassArray** structure is passed as a parameter in the following methods: 
  
- [IMAPIFormContainer::ResolveMultipleMessageClasses](imapiformcontainer-resolvemultiplemessageclasses.md)
    
- [IMAPIFormMgr::ResolveMultipleMessageClasses](imapiformmgr-resolvemultiplemessageclasses.md)
    
## See also

#### Concepts

[MAPI Structures](mapi-structures.md)

