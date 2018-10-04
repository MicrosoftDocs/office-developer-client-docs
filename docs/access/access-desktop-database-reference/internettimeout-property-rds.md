---
title: InternetTimeout Property (RDS)
TOCTitle: InternetTimeout Property (RDS)
ms:assetid: 66fc6e87-3d23-ce2c-18f5-0fc83ac43801
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249401(v=office.15)
ms:contentKeyID: 48545353
ms.date: 09/18/2015
mtps_version: v=office.15
---

# InternetTimeout Property (RDS)


**Applies to**: Access 2013 | Office 2013

Indicates the number of milliseconds to wait before a request times out.

## Settings and Return Values

Sets or returns a **Long** value that represents the number of milliseconds before a request will time out.

## Remarks

This property applies only to requests sent with the HTTP or HTTPS protocols.

Requests in a three-tier environment can take several minutes to execute. Use this property to specify additional time for long-running requests.

