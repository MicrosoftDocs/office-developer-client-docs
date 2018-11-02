---
title: TableDef.DateCreated property (DAO)
TOCTitle: DateCreated Property
ms:assetid: fedd28e9-41a4-db7f-9ba9-6ada350d594a
ms:mtpsurl: https://msdn.microsoft.com/library/Ff837292(v=office.15)
ms:contentKeyID: 48548947
ms.date: 09/18/2015
mtps_version: v=office.15
---

# TableDef.DateCreated property (DAO)


**Applies to**: Access 2013, Office 2013

Returns the date and time that an object was created (Microsoft Access workspaces only). Read-only **Variant**.

## Syntax

*expression* .DateCreated

*expression* A variable that represents a **TableDef** object.

## Remarks

**DateCreated** and **LastUpdated** return the date and time that the object was created or last updated. In a multiuser environment, users should get these settings directly from the file server to avoid discrepancies in the DateCreated and LastUpdated property settings.

