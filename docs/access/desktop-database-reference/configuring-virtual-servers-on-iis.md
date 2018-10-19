---
title: Configuring Virtual Servers on IIS
TOCTitle: Configuring Virtual Servers on IIS
ms:assetid: 0a8057a2-c90b-d0b5-21c8-5343e80708ce
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248837(v=office.15)
ms:contentKeyID: 48543154
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Configuring Virtual Servers on IIS


**Applies to**: Access 2013, Office 2013

When creating virtual servers in Internet Information Services 4.0, the following two extra steps are needed in order to configure the virtual server to work with RDS:

1.  When setting up the server, check "Allow Execute Access."

2.  Move msadcs.dll to *vroot*\\msadc, where *vroot* is the home directory of your virtual server.

