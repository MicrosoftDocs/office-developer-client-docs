---
title: SortColumn Property (RDS)
TOCTitle: SortColumn Property (RDS)
ms:assetid: 0a5d157c-9261-960d-6f89-33d9c94b3940
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248835(v=office.15)
ms:contentKeyID: 48543151
ms.date: 09/18/2015
mtps_version: v=office.15
---

# SortColumn Property (RDS)


**Applies to**: Access 2013, Office 2013

Indicates by which column to sort the records.

## Syntax

*DataControl*.SortColumn = *String*

## Parameters

  - *DataControl*

  - An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object.

  - *String*

  - A **String** value that represents the name or alias of the column by which to sort the records.

## Remarks

The **SortColumn**, [SortDirection](sortdirection-property-rds.md), [FilterValue](filtervalue-property-rds.md), [FilterCriterion](filtercriterion-property-rds.md), and [FilterColumn](filtercolumn-property-rds.md) properties provide sorting and filtering functionality on the client-side cache. The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on find criteria, while the full [Recordset](recordset-object-ado.md) is maintained in the cache. The [Reset](reset-method-rds.md) method will execute the criteria and replace the current **Recordset** with an updatable **Recordset**.

To sort on a **Recordset**, you must first save any pending changes. If you are using the **RDS.DataControl**, you can use the [SubmitChanges](submitchanges-method-rds.md) method. For example, if your **RDS.DataControl** is named ADC1, your code would be ADC1.SubmitChanges . If you are using an ADO **Recordset**, you can use its [UpdateBatch](updatebatch-method-ado.md) method. Using **UpdateBatch** is the recommended method for **Recordset** objects created with the [CreateRecordset](createrecordset-method-rds.md) method. For example, your code could be myRS.UpdateBatch or . If you are using an ADO **Recordset**, you can use its [UpdateBatch](updatebatch-method-ado.md) method. Using **UpdateBatch** is the recommended method for **Recordset** objects created with the [CreateRecordset](createrecordset-method-rds.md) method. For example, your code could be myRS.UpdateBatch or ADC1.Recordset.UpdateBatch .

