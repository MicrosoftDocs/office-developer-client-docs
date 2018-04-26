---
title: "Configuring Virtual Servers on IIS"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 0a8057a2-c90b-d0b5-21c8-5343e80708ce
description: "When creating virtual servers in Internet Information Services 4.0, the following two extra steps are needed in order to configure the virtual server to work with RDS:"
---

# Configuring Virtual Servers on IIS

When creating virtual servers in Internet Information Services 4.0, the following two extra steps are needed in order to configure the virtual server to work with RDS:
  
1. When setting up the server, check "Allow Execute Access."
    
2. Move msadcs.dll to  *vroot*  \msadc, where  *vroot*  is the home directory of your virtual server. 
    

