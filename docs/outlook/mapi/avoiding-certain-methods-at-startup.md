---
title: "Avoiding Certain Methods at Startup"
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7bb86fc8-d1ae-4937-9919-86c3a0f5651d
description: "Last modified: December 07, 2015"
 
 
---

# Avoiding Certain Methods at Startup

 
  
**Applies to**: Outlook 
  
To improve performance at startup time, avoid making the following calls:
  
- [IMAPISession::EnumAdrTypes](imapisession-enumadrtypes.md)
    
- [IMAPISession::GetStatusTable](imapisession-getstatustable.md)
    
- [IMAPISession::Logoff](imapisession-logoff.md)
    
- [IMAPISession::QueryIdentity](imapisession-queryidentity.md)
    
- [IMAPIStatus::ValidateState](imapistatus-validatestate.md)
    
The call to **IMAPIStatus::ValidateState** affects performance only when made on either the MAPI spooler or the MAPI subsystem. The reason that these methods slow startup processing is because they cannot complete until the MAPI spooler has finished its startup tasks. 
  
You should also avoid searching the message store at startup time. Make your [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) call when startup processing has finished. 
  

