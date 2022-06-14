---
title: Comparison of Microsoft Access SQL and ANSI SQL
TOCTitle: Comparison of Microsoft Access SQL and ANSI SQL
ms:assetid: 0686f98f-10fe-0e02-e9d1-84ff3e755b57
ms:mtpsurl: https://msdn.microsoft.com/library/Ff844937(v=office.15)
ms:contentKeyID: 48543052
ms.date: 06/13/2019
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Comparison of Microsoft Access SQL and ANSI SQL

**Applies to**: Access 2013, Office 2013

Microsoft Access database engine SQL is generally ANSI-89 Level 1 compliant. However, certain ANSI SQL features are not implemented in Microsoft Access SQL. Conversely, Microsoft Access SQL includes reserved words and features not supported in ANSI SQL.

## Major differences

- Microsoft Access SQL and ANSI SQL each have different reserved words and data types. For more information, see [Microsoft Access Database Engine SQL Reserved Words](sql-reserved-words.md) and [Equivalent ANSI SQL Data Types](equivalent-ansi-sql-data-types.md). Using the Microsoft Access Database Engine OLE DB Provider there are additional reserved words.

- **[Between…And](/office/vba/access/concepts/miscellaneous/between-and-operator)**
    
  *expr1* \[NOT\] **Between** *value1* **And** *value2*
    
  In Microsoft Access SQL, *value1* can be greater than *value2*; in ANSI SQL, *value1* must be equal to or less than *value2.*

- Microsoft Access SQL supports both ANSI SQL wildcard characters and [wildcard characters](using-wildcard-characters-in-string-comparisons.md) that are specific to the Microsoft Access database engine to use with the **[Like](/office/vba/access/Concepts/Structured-Query-Language/like-operator-microsoft-access-sql)** operator. The use of the ANSI and Microsoft Access database engine wildcard characters is mutually exclusive. You must use one set or the other and cannot mix them. The ANSI SQL wildcards are only available when using the Microsoft Access database engine and the Microsoft Access Database Engine OLE DB Provider. If you try to use the ANSI SQL wildcards through Microsoft Access or DAO, then they will be interpreted as literals. The opposite is true when using the Microsoft Access Database Engine OLE DB Provider.
    
    <table>
    <colgroup>
    <col />
    <col />
    <col />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Matching character</p></th>
    <th><p>Microsoft Access SQL</p></th>
    <th><p>ANSI SQL</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Any single character</p></td>
    <td><p>?</p></td>
    <td><p>_ (underscore)</p></td>
    </tr>
    <tr class="even">
    <td><p>Zero or more characters</p></td>
    <td><p>*</p></td>
    <td><p>%</p></td>
    </tr>
    </tbody>
    </table>


- Microsoft Access SQL is generally less restrictive. For example, it permits grouping and ordering on expressions.

- Microsoft Access SQL supports more powerful expressions.

## Enhanced features of Microsoft Access SQL

Microsoft Access SQL provides the following enhanced features:

- The [TRANSFORM](transform-statement-microsoft-access-sql.md) statement, which provides support for crosstab queries.

- Additional [aggregate functions](sql-aggregate-functions-sql.md), such as **StDev** and **VarP**.

- The [PARAMETERS](parameters-declaration-microsoft-access-sql.md) declaration for defining parameter queries.

## ANSI SQL features not supported in Microsoft Access SQL

Microsoft Access SQL does not support the following ANSI SQL features:

- DISTINCT aggregate function references. For example, Microsoft Access SQL does not allow SUM(DISTINCT *columnname*).

- The LIMIT TO *nn* ROWS clause used to limit the number of rows returned by a query. You can use only the [WHERE clause](/office/vba/access/Concepts/Structured-Query-Language/where-clause-microsoft-access-sql) to limit the scope of a query.
