---
title: "FilterColumn Property (RDS)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fb5d9f23-b62a-8131-d6ff-8b7ed8bb825c

---

# FilterColumn Property (RDS)

Indicates the column on which to evaluate the filter criteria.
  
## Syntax

 *DataControl*  . **FilterColumn** =  *String* 
  
## Parameters

-  *DataControl* 
    
- An object variable that represents an [RDS.DataControl](datacontrol-object-rds.md) object. 
    
-  *String* 
    
- A **String** value that specifies the column on which to evaluate the filter criteria. The filter criteria are specified in the [FilterCriterion](filtercriterion-property-rds.md) property. 
    
## Remarks

The [SortColumn](sortcolumn-property-rds.md), [SortDirection](sortdirection-property-rds.md), [FilterValue](filtervalue-property-rds.md), [FilterCriterion](filtercriterion-property-rds.md), and **FilterColumn** properties provide sorting and filtering functionality on the client-side cache. The sorting functionality orders records by values from one column. The filtering functionality displays a subset of records based on find criteria, while the full [Recordset](recordset-object-ado.md) is maintained in the cache. The [Reset](reset-method-rds.md) method will execute the criteria and replace the current **Recordset** with an updatable **Recordset**. 
  

