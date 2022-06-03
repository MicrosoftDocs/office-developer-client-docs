---
title: SQL expressions (Access desktop database reference)
TOCTitle: SQL expressions
ms:assetid: 91722f18-8589-d9fc-79ef-0be4ab11f822
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197629(v=office.15)
ms:contentKeyID: 48546349
ms.date: 06/13/2019
mtps_version: v=office.15
ms.localizationpriority: high
---

# SQL expressions

**Applies to**: Access 2013, Office 2013

An SQL expression is a string that makes up all or part of an SQL statement. For example, the **FindFirst** method on a **Recordset** object uses an SQL expression consisting of the selection criteria found in an SQL [WHERE clause](https://docs.microsoft.com/office/vba/access/Concepts/Structured-Query-Language/where-clause-microsoft-access-sql).

The Microsoft Access database engine uses the Microsoft Visual Basic for Applications (VBA) expression service to perform simple arithmetic and function evaluation. All of the operators used in Microsoft Access database engine SQL expressions (except **[Between](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/between-and-operator)**, **[In](/office/vba/access/concepts/miscellaneous/in-operator-microsoft-access-sql)**, and **[Like](https://docs.microsoft.com/office/vba/access/Concepts/Structured-Query-Language/like-operator-microsoft-access-sql)**) are defined by the VBA expression service. 

In addition, the VBA expression service offers over 100 VBA functions that you can use in SQL expressions. For example, you can use these VBA functions to compose an SQL query in the Microsoft Access query Design view, and you can also use these functions in an SQL query in the DAO **OpenRecordset** method in Microsoft Visual C++, Microsoft Visual Basic, and Microsoft Excel code.

## See also

- [Access VBA Concepts](/office/vba/access/concepts/miscellaneous/concepts-access-vba-reference)
