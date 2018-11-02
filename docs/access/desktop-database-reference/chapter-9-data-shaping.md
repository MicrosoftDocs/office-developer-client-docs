---
title: 'Chapter 9: Data shaping'
TOCTitle: 'Chapter 9: Data shaping'
ms:assetid: f66a319f-1b3d-c4a3-50b3-af1a47540832
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250253(v=office.15)
ms:contentKeyID: 48548739
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Chapter 9: Data shaping

**Applies to**: Access 2013, Office 2013

*Data shaping* provides a way to query a data source and return a [Recordset](recordset-object-ado.md) that represents a parent-child relationship between two or more logical entities (a hierarchy). 

A classic example of a hierarchical relationship is customers and orders. For every customer in a database, there can be zero or more orders. Regular SQL provides a means of retrieving the data using JOIN syntax, but this can be inefficient and unwieldy because redundant parent data is repeated in each record returned for a given parent-child relationship. Data shaping can relate a single parent record in the parent **Recordset** to multiple child records in the child **Recordset**, avoiding the redundancy of a JOIN. Most people find the parent-child multiple **Recordset** programming model more natural and easier to work with than the single **Recordset** JOIN model.

The data shaping syntax also provides other capabilities. Developers can create new **Recordset** objects without an underlying data source by using the NEW keyword to describe the fields of the parent and child **Recordsets**. The new **Recordset** object can be populated with data and persistently stored. Developers can also perform various calculations or aggregations (for example, SUM, AVG, and MAX) on child fields. Data shaping can also create a parent **Recordset** from a child **Recordset** by grouping records in the child and placing one row in the parent for each group in the child.

See the following topics to learn more about data shaping:

- [Required providers for data shaping](required-providers-for-data-shaping.md)
- [Shape Compute clause](shape-compute-clause.md)
- [Fabricating hierarchical Recordsets](fabricating-hierarchical-recordsets.md)
- [Accessing rows in a hierarchical Recordset](accessing-rows-in-a-hierarchical-recordset.md)
- [Formal shape grammar](formal-shape-grammar.md)
- [Visual Basic for Applications functions](visual-basic-for-applications-functions.md)
- [Shape Append clause (ADO)](shape-append-clause.md)
- [Data shaping (ADO)](data-shaping.md)
- [Shape commands in general (ADO)](shape-commands-in-general.md)

