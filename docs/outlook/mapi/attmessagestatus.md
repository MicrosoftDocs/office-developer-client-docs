---
title: "attMessageStatus"
description: "Describes the MessageStatus attribute and provides a list of MAPI message and TNEF flags."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 8f55470a-65b3-4210-a7d2-9031cb17ca80
 
 
---

# attMessageStatus

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI message flags are mapped to TNEF flags to preserve backward compatibility. All the flags are grouped together and encoded in a single byte. The mappings are as follows:
  
|**MAPI message flags**|**TNEF flags**|
|:-----|:-----|
|MSGFLAG_READ  <br/> |fmsRead  <br/> |
|MSGFLAG_UNMODIFED  <br/> |~fmsModified  <br/> |
|MSGFLAG_SUBMIT  <br/> |fmsSubmitted  <br/> |
|MSGFLAG_HASATTACH  <br/> |fmsHasAttach  <br/> |
|MSGFLAG_UNSENT  <br/> |fmsLocal  <br/> |
   
These flags are defined in the TNEF.H header file.
  

