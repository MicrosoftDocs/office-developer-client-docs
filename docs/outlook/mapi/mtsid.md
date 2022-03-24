---
title: "MTSID"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.MTSID
api_type:
- COM
ms.assetid: 3d9bc643-332f-4c8e-83e6-ce9b15711945
description: "Last modified: March 09, 2015"
---

# MTSID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an X.400 message transport system (MTS) entry identifier. 
  
|Property|Description|
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbMTSID](cbmtsid.md), [CbNewMTSID](cbnewmtsid.md) <br/> |
   
```cpp
typedef struct
{
  ULONG cb;
  BYTE abEntry[MAPI_DIM];
} MTSID, FAR *LPMTSID;

```

## Members

 **cb**
  
> Count of bytes in the array described by the **abEntry** member. 
    
 **abEntry**
  
> Byte array that contains the MTS entry identifier data.
    
## Remarks

The **MTSID** structure is used only for X.400 mappings of MAPI entry identifiers. It corresponds to the MAPI [FLATENTRY](flatentry.md) structure. 
  
An MTS identifier has the same format as a MAPI entry identifier or a binary property value. MTS identifiers can be particularly useful for canceling deferred messages. 
  
## See also



[FLATENTRY](flatentry.md)
  
[FLATMTSIDLIST](flatmtsidlist.md)


[MAPI Structures](mapi-structures.md)

