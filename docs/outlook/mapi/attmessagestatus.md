---
title: "attMessageStatus"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 8f55470a-65b3-4210-a7d2-9031cb17ca80
description: "Last modified: March 09, 2015"
---

# attMessageStatus

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
MAPI message flags are mapped to TNEF flags to preserve backward compatibility. All the flags are grouped together and encoded in a single byte. The mappings are as follows:
  
|**MAPI message flags**|**TNEF flags**|
|:-----|:-----|
|MSGFLAG_READ  <br/> |fmsRead  <br/> |
|MSGFLAG_UNMODIFED  <br/> |~fmsModified  <br/> |
|MSGFLAG_SUBMIT  <br/> |fmsSubmitted  <br/> |
|MSGFLAG_HASATTACH  <br/> |fmsHasAttach  <br/> |
|MSGFLAG_UNSENT  <br/> |fmsLocal  <br/> |
   
These flags are defined in the TNEF.H header file.
  

