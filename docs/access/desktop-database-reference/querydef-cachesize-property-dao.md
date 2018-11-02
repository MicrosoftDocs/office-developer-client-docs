---
title: QueryDef.CacheSize property (DAO)
TOCTitle: CacheSize Property
ms:assetid: a84d990e-8180-daa3-7640-47d2be8fd28b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff821397(v=office.15)
ms:contentKeyID: 48546899
ms.date: 09/18/2015
mtps_version: v=office.15
---

# QueryDef.CacheSize property (DAO)


**Applies to**: Access 2013, Office 2013

Sets or returns the number of records retrieved from an ODBC data source that will be cached locally. Read/write **Long**.

## Syntax

*expression* .CacheSize

*expression* A variable that represents a **QueryDef** object.

## Remarks

The value of the **CacheSize** property must be between 5 and 1200, but not greater than available memory will allow. A typical value is 100. A setting of 0 turns off caching.

The Microsoft Access database engine requests records within the cache range from the cache, and it requests records outside the cache range from the server.

Records retrieved from the cache don't reflect concurrent changes that other users made to the source data.

