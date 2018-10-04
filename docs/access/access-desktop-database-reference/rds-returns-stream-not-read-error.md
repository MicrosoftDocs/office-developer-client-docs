---
title: RDS Returns "Stream Not Read" Error
TOCTitle: RDS Returns "Stream Not Read" Error
ms:assetid: 325f7b9d-8e71-bc2c-94e3-b4b4a1a2dc58
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249097(v=office.15)
ms:contentKeyID: 48544075
ms.date: 09/18/2015
mtps_version: v=office.15
---

# RDS Returns \"Stream Not Read\" Error


_**Applies to:** Access 2013 | Office 2013_

"The Stream object could not be read because it is empty, or the current position is at the end of the Stream. For non-empty Streams, set the current position with the Position property. To determine if a Stream is empty, check the Size property."

If you get the error above, it may be a result of trying to use a parameterized hierarchical query over http. RDS does not permit you to remote parameterized hierarchies.

