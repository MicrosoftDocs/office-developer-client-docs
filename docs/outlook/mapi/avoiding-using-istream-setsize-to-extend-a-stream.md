---
title: "Avoiding Using IStreamSetSize to Extend a Stream"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: b6de594f-e331-4421-956b-86ee0b5518fe
description: "Last modified: July 23, 2011"
---

# Avoiding Using IStream::SetSize to Extend a Stream

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
When writing to streams, it is sometimes necessary to enlarge them because their initial size is no longer sufficient. Use the OLE method **IStream::Write** to accomplish this rather than **IStream::SetSize**. **IStream::Write** automatically extends the stream, making ** IStream::SetSize ** unnecessary. Calling **IStream::Write** without **IStream::SetSize** can be up to three times faster than making the **SetSize** call prior to **Write**.
  

