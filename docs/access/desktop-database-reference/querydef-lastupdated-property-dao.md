---
title: QueryDef.LastUpdated Property (DAO)
TOCTitle: LastUpdated Property
ms:assetid: 3b7818d4-054e-54e2-bf63-58b340bb4a90
ms:mtpsurl: https://msdn.microsoft.com/library/Ff192665(v=office.15)
ms:contentKeyID: 48544287
ms.date: 09/18/2015
mtps_version: v=office.15
---

# QueryDef.LastUpdated Property (DAO)


**Applies to**: Access 2013 | Office 2013

Returns the date and time of the most recent change made to an object. Read-only **Variant**.

## Syntax

*expression* .LastUpdated

*expression* A variable that represents a **QueryDef** object.

## Remarks

**DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings.

