---
title: "Comparison of Microsoft Access SQL and ANSI SQL"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 0686f98f-10fe-0e02-e9d1-84ff3e755b57
description: "Microsoft Access database engine SQL is generally ANSI-89 Level 1 compliant. However, certain ANSI SQL features are not implemented in Microsoft® Access SQL. Conversely, Microsoft Access SQL includes reserved words and features not supported in ANSI SQL."
---

# Comparison of Microsoft Access SQL and ANSI SQL

Microsoft Access database engine SQL is generally ANSI-89 Level 1 compliant. However, certain ANSI SQL features are not implemented in Microsoft® Access SQL. Conversely, Microsoft Access SQL includes reserved words and features not supported in ANSI SQL.
  
## Major Differences

- Microsoft Access SQL and ANSI SQL each have different reserved words and data types. For more information, see [Microsoft Access Database Engine SQL Reserved Words](sql-reserved-words.md) and [Equivalent ANSI SQL Data Types](equivalent-ansi-sql-data-types.md). Using the Microsoft Access Database Engine OLE DB Provider there are additional reserved words.
    
- **[Between…And](http://msdn.microsoft.com/library/33a49af8-25f4-b107-e0e2-17c90d80c66a%28Office.15%29.aspx)**
    
     *expr1*  [NOT] **Between** *value1* **And** *value2* 
    
    In Microsoft Access SQL,  *value1*  can be greater than  *value2*  ; in ANSI SQL,  *value1*  must be equal to or less than  *value2.* 
    
- Microsoft Access SQL supports both ANSI SQL wildcard characters and [wildcard characters](using-wildcard-characters-in-string-comparisons.md) that are specific to the Microsoft Access database engine to use with the **[Like](http://msdn.microsoft.com/library/70d2ecef-90d7-aff9-398e-8703fb7dfc6e%28Office.15%29.aspx)** operator. The use of the ANSI and Microsoft Access database engine wildcard characters is mutually exclusive. You must use one set or the other and cannot mix them. The ANSI SQL wildcards are only available when using the Microsoft Access database engine and the Microsoft Access Database Engine OLE DB Provider. If you try to use the ANSI SQL wildcards through Microsoft Access or DAO, then they will be interpreted as literals. The opposite is true when using the Microsoft Access Database Engine OLE DB Provider. 
    
|**Matching character**|**Microsoft Access SQL**|**ANSI SQL**|
|:-----|:-----|:-----|
|Any single character  <br/> |?  <br/> |_ (underscore)  <br/> |
|Zero or more characters  <br/> |\*  <br/> |%  <br/> |
   
- Microsoft Access SQL is generally less restrictive. For example, it permits grouping and ordering on expressions.
    
- Microsoft Access SQL supports more powerful expressions.
    
## Enhanced Features of Microsoft Access SQL

Microsoft Access SQL provides the following enhanced features:
  
- The [TRANSFORM](transform-statement-microsoft-access-sql.md) statement, which provides support for crosstab queries. 
    
- Additional [aggregate functions](sql-aggregate-functions-sql.md), such as **StDev** and **VarP**. 
    
- The [PARAMETERS](parameters-declaration-microsoft-access-sql.md) declaration for defining parameter queries. 
    
## ANSI SQL Features Not Supported in Microsoft Access SQL

Microsoft Access SQL does not support the following ANSI SQL features:
  
- DISTINCT aggregate function references. For example, Microsoft Access SQL does not allow SUM(DISTINCT  *columnname*  ). 
    
- The LIMIT TO  *nn*  ROWS clause used to limit the number of rows returned by a query. You can use only the [WHERE clause](http://msdn.microsoft.com/library/67e4caed-6512-e8bd-39d0-6dca18114b18%28Office.15%29.aspx) to limit the scope of a query. 
    

