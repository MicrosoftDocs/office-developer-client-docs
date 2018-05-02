---
title: "Initializing OLE for MAPI"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 53b65299-69f8-4fc0-8d9b-f666e814aaac
description: "Last modified: July 23, 2011"
 
 
---

# Initializing OLE for MAPI

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
If you also use OLE, call the OLE function [OleInitialize](http://msdn.microsoft.com/en-us/library/ms690134%28v=VS.85%29.aspx) to initialize the OLE libraries. **OleInitialize** initializes global data for the session and prepares the OLE libraries to accept calls. For information about calling **OleInitialize**, see the Windows SDK.
  

