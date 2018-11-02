---
title: FilterValue property (RDS)
TOCTitle: FilterValue property (RDS)
ms:assetid: 66dc14cd-cc14-78cb-cb05-91eefb17ea47
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249399(v=office.15)
ms:contentKeyID: 48545350
ms.date: 09/18/2015
mtps_version: v=office.15
---

# FilterValue property (RDS)


**Applies to**: Access 2013, Office 2013


Indicates the value with which to filter records.

## Syntax

*DataControl*.FilterValue = *String*

## Parameters

  - *DataControl*

  - An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.

  - *String*

  - A **String** value that represents a data value with which to filter records (for example, 'Programmer' or 125 ).

## Remarks

The [SortColumn](sortcolumn-property-rds.md), [SortDirection](sortdirection-property-rds.md), **FilterValue**, [FilterCriterion](filtercriterion-property-rds.md), and [FilterColumn](filtercolumn-property-rds.md) properties provide sorting and filtering functionality on the client-side cache. The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on find criteria, while the full [Recordset](recordset-object-ado.md) is maintained in the cache. The [Reset](reset-method-rds.md) method will execute the criteria and replace the current **Recordset** with an updatable **Recordset**.

Null values result in a type mismatch error.

