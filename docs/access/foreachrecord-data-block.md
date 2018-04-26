---
title: "ForEachRecord Data Block"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: be369196-230e-1f92-e36b-667048eef2be

description: "A ForEachRecord data block repeats a set of statements for each record in a domain."
---

# ForEachRecord Data Block

A **ForEachRecord** data block repeats a set of statements for each record in a domain. 
  
> [!NOTE]
> The **ForEachRecord** data block is available only in Data Macros. 
  
## Setting

The **ForEachRecord** action has the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
|**In** <br/> |Yes  <br/> |A string that identifies the domain of records to operate on. The  *In*  argument can contain the name of the table, a select query, or a SQL statement.  <br/> > [!NOTE]> The specified domain cannot include data stored in a linked table or ODBC data source.           |
|**Where Condition** <br/> |No  <br/> |A string expression used to restrict the range of data on which the **ForEachRecord** data block is performed. For example, criteria is often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria is omitted, the **ForEachRecord** data block operates on the entire domain specified by the  *In*  argument. Any field that is included in criteria must also be a field in  *In*  .  <br/> |
|**Alias** <br/> |No  <br/> |A string that provides an alternative name for the domain specified by the  *In*  argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references.If  *Alias*  is not specified, the table or query name will be used as the alias.  <br/> |
   
## Remarks

Use the **[ExitForEachRecord](exitforeachrecord-macro-action.md)** action to exit a **ForEachRecord** data block immediately. 
  

