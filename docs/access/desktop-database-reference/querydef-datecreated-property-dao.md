---
title: QueryDef.DateCreated property (DAO)
TOCTitle: DateCreated Property
ms:assetid: f7585b34-8314-fb9f-daa6-cd1a8ad59d91
ms:mtpsurl: https://msdn.microsoft.com/library/Ff836910(v=office.15)
ms:contentKeyID: 48548763
ms.date: 09/18/2015
mtps_version: v=office.15
localization_priority: Normal
---

# QueryDef.DateCreated property (DAO)


**Applies to**: Access 2013, Office 2013

Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only **Variant**.

## Syntax

*expression* .DateCreated

*expression* A variable that represents a **QueryDef** object.

## Remarks

**DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings.

