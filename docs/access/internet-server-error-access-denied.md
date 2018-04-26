---
title: "Internet Server Error Access Denied"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 65f4608b-afec-2867-dae3-e29bae03a6fd
description: "If you get this error, it usually means that Microsoft Internet Information Services (IIS) returned the following status:"
---

# Internet Server Error: Access Denied

If you get this error, it usually means that Microsoft Internet Information Services (IIS) returned the following status:
  
HTTP_STATUS_DENIED 401
  
Make sure the directories accessed by IIS have proper permissions. RDS can communicate with an IIS Web server running in any one of the three Password Authentication modes: Anonymous, Basic, or NT Challenge/Response (called Integrated Windows authentication in Windows 2000). Also, the Web server must have permissions to the data source computer if it is a Windows NT/Windows 2000 computer.
  

