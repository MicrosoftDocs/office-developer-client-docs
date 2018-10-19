---
title: TableDef.LastUpdated Property (DAO)
TOCTitle: LastUpdated Property
ms:assetid: fafe54e2-2cf0-5874-92b9-6e20a65e77ef
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837164(v=office.15)
ms:contentKeyID: 48548859
ms.date: 09/18/2015
mtps_version: v=office.15
---

# TableDef.LastUpdated Property (DAO)


**Applies to**: Access 2013, Office 2013

Returns the date and time of the most recent change made to an object. Read-only **Variant**.

## Syntax

*expression* .LastUpdated

*expression* A variable that represents a **TableDef** object.

## Remarks

**DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings.

