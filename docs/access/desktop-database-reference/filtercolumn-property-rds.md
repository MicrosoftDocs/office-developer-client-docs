---
title: FilterColumn property (RDS)
TOCTitle: FilterColumn property (RDS)
ms:assetid: fb5d9f23-b62a-8131-d6ff-8b7ed8bb825c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ250287(v=office.15)
ms:contentKeyID: 48548868
ms.date: 09/18/2015
mtps_version: v=office.15
ms.localizationpriority: medium
---

# FilterColumn property (RDS)

**Applies to**: Access 2013, Office 2013

Indicates the column on which to evaluate the filter criteria.

## Syntax

*DataControl*.FilterColumn = *String*

## Parameters

|Parameter|Description|
|:--------|:----------|
|*DataControl* |An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.|
|*String* |A **String** value that specifies the column on which to evaluate the filter criteria. The filter criteria are specified in the [FilterCriterion](filtercriterion-property-rds.md) property.|

## Remarks

The [SortColumn](sortcolumn-property-rds.md), [SortDirection](sortdirection-property-rds.md), [FilterValue](filtervalue-property-rds.md), [FilterCriterion](filtercriterion-property-rds.md), and **FilterColumn** properties provide sorting and filtering functionality on the client-side cache. 

The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on find criteria, while the full [Recordset](recordset-object-ado.md) is maintained in the cache. 

The [Reset](reset-method-rds.md) method will execute the criteria and replace the current **Recordset** with an updatable **Recordset**.

