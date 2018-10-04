---
title: Document.LastUpdated Property (DAO)
TOCTitle: LastUpdated Property
ms:assetid: 9307ceee-095f-0364-fd5b-905bc523b9c0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197661(v=office.15)
ms:contentKeyID: 48546388
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Document.LastUpdated Property (DAO)


**Applies to**: Access 2013 | Office 2013

Returns the date and time of the most recent change made to an object. Read-only **Variant**.

## Syntax

*expression* .LastUpdated

*expression* A variable that represents a **Document** object.

## Remarks

**DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings.

