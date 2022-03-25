---
title: "SSubRestriction" 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SSubRestriction
api_type:
- COM
ms.assetid: 5f7012f7-060d-4f2d-bcff-2aa9f6980e71
description: "Describes a sub-object restriction which is used to filter the rows of a message's attachment or recipient table."
---

# SSubRestriction

**Applies to**: Outlook 2013 | Outlook 2016
  
Describes a sub-object restriction which is used to filter the rows of a message's attachment or recipient table.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |

```cpp
typedef struct _SSubRestriction
{
  ULONG ulSubObject;
  LPSRestriction lpRes;
} SSubRestriction;

```

## Members

 **ulSubObject**
  
> Type of sub-object to serve as the target for the restriction. Possible values are as follows:

PR_MESSAGE_RECIPIENTS
  
> Apply the restriction to a message's recipient table.

PR_MESSAGE_ATTACHMENTS
  
> Apply the restriction to a message's attachment table.

 **lpRes**
  
> Pointer to an [SRestriction](srestriction.md) structure.

## Remarks

Sub-object restrictions are not supported by all tables. Typically, only folder contents tables and search results folders support them. For example, sub-object restrictions are used to find a message that has a particular type of attachment or recipient.
  
If an implementation does not support sub-object restrictions, it returns MAPI_E_TOO_COMPLEX from its [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md) methods.
  
For a general discussion of how restrictions work, see [About Restrictions](about-restrictions.md).
  
## See also

[SRestriction](srestriction.md)
[MAPI Structures](mapi-structures.md)
