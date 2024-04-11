---
title: "OLE Attachments"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: febb6a5e-7c40-4f21-806e-7f827d1c37cf
 
 
---

# OLE Attachments

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Attachments that are OLE objects are encoded as OLE 1 stream objects for backward compatibility. If the original object is really an OLE 2 **IStorage** object, then the object must be converted to an OLE 1 stream. This conversion is performed using the **OleConvertIStorageToOLESTREAM** function, which is part of the Win32 OLE libraries. 
  

