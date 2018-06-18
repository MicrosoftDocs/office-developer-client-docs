---
title: "FLATMTSIDLIST"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FLATMTSIDLIST
api_type:
- COM
ms.assetid: b66c2815-72bc-4535-b34c-899bb830f29e
description: "Last modified: March 09, 2015"
---

# FLATMTSIDLIST

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of [MTSID](mtsid.md) structures, each of which contains an X.400 message transport system (MTS) entry identifier. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbFLATMTSIDLIST](cbflatmtsidlist.md), [CbNewFLATMTSIDLIST](cbnewflatmtsidlist.md) <br/> |
   
```cpp
typedef struct
{
  ULONG cMTSIDs;
  ULONG cbMTSIDs;
  BYTE abMTSIDs[MAPI_DIM];
} FLATMTSIDLIST, FAR *LPFLATMTSIDLIST;

```

## Members

 **cMTSIDs**
  
> Count of **MTSID** structures in the array described by the **abMTSIDs** member. 
    
 **cbMTSIDs**
  
> Count of bytes in the array described by **abMTSIDs**.
    
 **abMTSIDs**
  
> Byte array that contains one or more **MTSID** structures. 
    
## Remarks

The **FLATMTSIDLIST** structure's use in X.400 messaging corresponds to the [FLATENTRYLIST](flatentrylist.md) structure's use in MAPI messaging. MAPI uses **FLATMTSIDLIST** structures to maintain X.400 properties during message handling. Service providers use **FLATMTSIDLIST** structures when handling incoming and outgoing X.400 messages. 
  
In the **abMTSIDs** array, each **MTSID** structure is aligned on a naturally aligned boundary. Extra bytes are included as padding to make sure natural alignment between any two **MTSID** structures. The first **MTSID** structure in the array is always aligned correctly because the offset of the **abMTSIDs** member is 8. To compute the offset of the next structure, use the size of the first entry rounded up to the next multiple of 4. Use the [CbNewMTSID](cbnewmtsid.md) macro to compute the size of an **MTSID** structure. 
  
## See also



[CbNewFLATMTSIDLIST](cbnewflatmtsidlist.md)
  
[FLATENTRYLIST](flatentrylist.md)
  
[MTSID](mtsid.md)


[MAPI Structures](mapi-structures.md)

