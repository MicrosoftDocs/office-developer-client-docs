---
title: "SCountRestriction"
manager: lindalu
ms.date: 12/27/2024
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SCountRestriction
api_type:
- COM
ms.assetid: d8961786-1686-4a90-b18e-ed56325fdb82
description: "Describes a count restriction, which is used to limit the number of times an (inner) restriction is evaluated."
---

# SCountRestriction

**Applies to**: Outlook 2013 | Outlook 2016

Describes a count restriction, which is used to limit the number of times an (inner) restriction is evaluated.

|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |

```cpp
typedef struct _SCountRestriction
{
  ULONG ulCount;
  LPSRestriction lpRes;
} SCountRestriction;
```

## Members

 **ulCount**

> When the restriction is evaluated, it shall match at most this many times.

 **lpRes**

> Pointer to an [SRestriction](srestriction.md) structure.

## Remarks

If an implementation does not support count restrictions, it returns MAPI_E_TOO_COMPLEX from its [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md) methods.

For a general discussion of how restrictions work, see [About Restrictions](about-restrictions.md).

## See also

[SRestriction](srestriction.md)
[MAPI Structures](mapi-structures.md)
