---
title: "IMAPIWaitResult : IUnknown" 
manager: lindalu
ms.date: 03/20/2021
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIWAITRESULT
api_type:
- COM
ms.assetid: d7157f57-709d-4e53-973b-176954e2bb73
description: "Last modified: March 30, 2021"
---

# IMAPIWAITRESULT : IUnknown
  
**Applies to**: Outlook 2013 | Outlook 2016 | Outlook 2019

IFACEMETHODIMP End() override

Called to initiate the blocking wait on the thread where it is called, does not need to be the same thread that called “BeginWait”.
  
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> |  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIWAITRESULT  <br/> |

## See also

[IMAPIINITMONITOR : IUnknown](imapiinitmonitoriunknown.md)