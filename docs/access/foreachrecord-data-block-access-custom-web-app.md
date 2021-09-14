---
title: "ForEachRecord Data Block (Access custom web app)"
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 8ffa0de2-5abb-4375-9fb5-042ce3c21506
description: "A ForEachRecord data block repeats a set of statements for each record in a domain."
---

# ForEachRecord Data Block (Access custom web app)

A **ForEachRecord** data block repeats a set of statements for each record in a domain. 
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
> [!NOTE]
> The **ForEachRecord** data block is available only in Data Macros. 
  
## Setting

The **ForEachRecord** action has the following arguments. 
  
|**Argument name**|**Required**|**Description**|
|:-----|:-----|:-----|
|**In** <br/> |Yes  <br/> |A string that identifies the domain of records to operate on. The  *In*  argument can contain the name of the table, a select query, or a SQL statement.  <br/> **NOTE**: The specified domain cannot include data stored in a linked table or ODBC data source.           |
|**Where Condition** <br/> |No  <br/> |A string expression used to restrict the range of data on which the **ForEachRecord** data block is performed. For example, criteria is often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria are omitted, the **ForEachRecord** data block operates on the entire domain specified by the  *In*  argument. Any field that is included in criteria must also be a field in  *In*  .  <br/> |
|**Alias** <br/> |No  <br/> |A string that provides an alternative name for the domain specified by the  *In*  argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references. If  *Alias*  is not specified, the table or query name will be used as the alias.  <br/> |
   
## Remarks

Use the **[ExitForEachRecord](exitforeachrecord-macro-action-access-custom-web-app.md)** action to exit a **ForEachRecord** data block immediately. 
  

