---
title: Recordset2.ParentRecordset Property (DAO)
TOCTitle: ParentRecordset Property
ms:assetid: 816cc92e-e530-6ca6-65b0-3165221835a6
ms:mtpsurl: https://msdn.microsoft.com/library/Ff196492(v=office.15)
ms:contentKeyID: 48545948
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1101188
f1_categories:
- Office.Version=v15
---

# Recordset2.ParentRecordset Property (DAO)


**Applies to**: Access 2013 | Office 2013 

Returns the parent **Recordset** of the specified recordset. Read-only.

## Version Information

Version Added: Access 2007

## Syntax

*expression* .ParentRecordset

*expression* A variable that represents a **Recordset2** object.

## Remarks

The **ParentRecordset** property returns **Null** if the specifed recordset does not represent a multi-valued field.

