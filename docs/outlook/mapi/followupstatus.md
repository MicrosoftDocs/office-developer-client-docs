---
title: "FollowUpStatus"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c3d0f6c4-4597-784f-8d44-6e5d905895b4
description: "Last modified: July 23, 2011"
---

# FollowUpStatus

  
  
**Applies to**: Outlook 
  
Specifies the different follow-up statuses for a message.
  
## Quick Info

```
enum FollowUpStatus { 
    flwupNone = 0, 
    flwupComplete, 
    flwupMarked, 
    flwupMAX}; 

```

## Members

 _flwupNone_
  
> No follow-up has been specified.
    
 _flwupComplete_
  
> The message is complete.
    
 _flwupMarked_
  
> The message is marked for follow-up.
    
 _flwupMAX_
  
> The number of different statuses supported for follow-up.
    
## See also

#### Reference

[PidTagFlagStatus Canonical Property](pidtagflagstatus-canonical-property.md)

