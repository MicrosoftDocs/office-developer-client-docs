---
title: "Creating a Message Subject"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 70e18534-054f-49e7-9a5d-10db0db132d0
description: "Last modified: July 23, 2011"
 
 
---

# Creating a Message Subject

  
  
**Applies to**: Outlook 
  
The subject of a message, **PR_SUBJECT** ([PidTagSubject](pidtagsubject-canonical-property.md)), is an optional property, used to summarize the intent of a message. If you choose to set it, make it a character string 128 bytes or less. The 128 byte limit is not a limit imposed by MAPI; it is a limit imposed by some message store providers. To ensure interoperability with providers that do impose it, limit subjects to 128 bytes. 
  
Be aware that some message store providers do not allow **PR_SUBJECT** to be written to a stream with the [IStream](http://msdn.microsoft.com/en-us/library/aa380034%28VS.85%29.aspx) interface. 
  
Do not set **PR_SUBJECT_PREFIX** ([PidTagSubjectPrefix](pidtagsubjectprefix-canonical-property.md)); this property is set only on replies and forwarded messages. 
  

