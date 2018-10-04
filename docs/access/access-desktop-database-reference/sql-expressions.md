---
title: SQL Expressions
TOCTitle: SQL Expressions
ms:assetid: 91722f18-8589-d9fc-79ef-0be4ab11f822
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff197629(v=office.15)
ms:contentKeyID: 48546349
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SQL Expressions


_**Applies to:** Access 2013 | Office 2013_

An SQL expression is a string that makes up all or part of an SQL statement. For example, the**FindFirst** method on a **Recordset** object uses an SQL expression consisting of the selection criteria found in an SQL [WHERE clause](https://msdn.microsoft.com/en-us/library/ff195245\(v=office.15\)).

The Microsoft Access database engine uses the Microsoft® Visual Basic® for Applications (or VBA) expression service to perform simple arithmetic and function evaluation. All of the operators used in Microsoft Access database engine SQL expressions (except **[Between](https://msdn.microsoft.com/en-us/library/ff192436\(v=office.15\))**, **[In](https://msdn.microsoft.com/en-us/library/ff836369\(v=office.15\))**, and **[Like](https://msdn.microsoft.com/en-us/library/ff195752\(v=office.15\))**) are defined by the VBA expression service. In addition, the VBA expression service offers over 100 VBA functions that you can use in SQL expressions. For example, you can use these VBA functions to compose an SQL query in the Microsoft Access query Design view, and you can also use these functions in an SQL query in the DAO **OpenRecordset** method in Microsoft Visual C++®, Microsoft Visual Basic, and Microsoft Excel code.

