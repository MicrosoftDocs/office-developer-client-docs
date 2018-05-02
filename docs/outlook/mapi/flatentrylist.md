---
title: "FLATENTRYLIST"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FLATENTRYLIST
api_type:
- COM
ms.assetid: b465d015-9b62-4986-b0df-118121f60602
description: "Last modified: March 09, 2015"
---

# FLATENTRYLIST

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an array of [FLATENTRY](flatentry.md) structures. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbFLATENTRYLIST](cbflatentrylist.md), [CbNewFLATENTRYLIST](cbnewflatentrylist.md) <br/> |
   
```
typedef struct
{
  ULONG cEntries;
  ULONG cbEntries;
  BYTE abEntries[MAPI_DIM];
} FLATENTRYLIST, FAR *LPFLATENTRYLIST;

```

## Members

 **cEntries**
  
> Count of **FLATENTRY** structures in the array described by the **abEntries** member. 
    
 **cbEntries**
  
> Count of bytes in the array described by **abEntries**. 
    
 **abEntries**
  
> Byte array that contains one or more **FLATENTRY** structures, arranged end to end. 
    
## Remarks

In the **abEntries** array, each **FLATENTRY** structure is aligned on a naturally aligned boundary. Extra bytes are included as padding to make sure natural alignment between any two **FLATENTRY** structures. The first **FLATENTRY** structure in the array is always aligned correctly because the offset of the **abEntries** member is 8. To compute the offset of the next structure, use the size of the first entry rounded up to the next multiple of 4. Use the [CbFLATENTRY](cbflatentry.md) macro to compute the size of a **FLATENTRY** structure. 
  
For example, the second **FLATENTRY** structure starts at an offset that consists of the offset of the first entry plus the length of the first entry rounded to the next four bytes. The length of the first entry is the length of its **cb** member plus the length of its **abEntry** member. 
  
The following code sample indicates how to compute offsets in a **FLATENTRYLIST** structure. Assume that  _lpFlatEntry_ is a pointer to the first structure in the list. 
  
```
(offsetof(lpFlatEntry->ab) // for example, 4
+ lpFlatEntry->cb // size of lpFlatEntry->ab 
+ 4) &amp; ~3 // round to next 4 byte boundary
```

## See also

#### Reference

[FLATENTRY](flatentry.md)
  
[PidTagReplyRecipientEntries Canonical Property](pidtagreplyrecipiententries-canonical-property.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

