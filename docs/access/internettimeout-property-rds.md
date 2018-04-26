---
title: "InternetTimeout Property (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 66fc6e87-3d23-ce2c-18f5-0fc83ac43801

---

# InternetTimeout Property (RDS)

Indicates the number of milliseconds to wait before a request times out.
  
## Settings and Return Values

Sets or returns a **Long** value that represents the number of milliseconds before a request will time out. 
  
## Remarks

This property applies only to requests sent with the HTTP or HTTPS protocols.
  
Requests in a three-tier environment can take several minutes to execute. Use this property to specify additional time for long-running requests.
  

