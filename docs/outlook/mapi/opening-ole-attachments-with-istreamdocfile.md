---
title: "Opening OLE Attachments with IStreamDocfile"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f91df63c-ff6d-4c63-a665-5bcfdabe7e0e
description: "Last modified: July 06, 2012"
 
 
---

# Opening OLE Attachments with IStreamDocfile

  
  
**Applies to**: Outlook 
  
When opening an OLE object attachment, use the **IStreamDocfile** interface rather than [IStream](http://msdn.microsoft.com/en-us/library/windows/desktop/aa380034%28v=vs.85%29.aspx) or [IStorage](http://msdn.microsoft.com/en-us/library/windows/desktop/aa380015%28v=vs.85%29.aspx). **IStreamDocfile** provides direct access to the object using structured storage, eliminating the need to perform a copy operation and reducing overhead. **IStreamDocfile** is a specific implementation of **IStream** with the content of the stream guaranteed to be formatted as structured storage. **IStreamDocfile** is implemented by message store providers. 
  

