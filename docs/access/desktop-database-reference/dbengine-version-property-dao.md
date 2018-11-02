---
title: DBEngine.Version property (DAO)
TOCTitle: Version Property
ms:assetid: b2807dc1-604f-4423-289a-ff38a3d9f31b
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822024(v=office.15)
ms:contentKeyID: 48547171
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1052986
f1_categories:
- Office.Version=v15
---

# DBEngine.Version property (DAO)


**Applies to**: Access 2013, Office 2013

Rreturns the version of DAO currently in use. Read-only **String**.

## Syntax

*expression* .Version

*expression* A variable that represents a **DBEngine** object.

## Remarks

The return value is a String that evaluates to a version number in the form "major.minor". For example, "3.0". The product version number consists of the version number (3), a period, and the release number (0).

