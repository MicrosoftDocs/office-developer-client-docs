---
title: "LookupRecord Data Block (Access custom web app)"
 
 
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
ms.topic: overview
  
ms.localizationpriority: medium
ms.assetid: 001899f7-5b1a-4c0b-a0e4-e01985eea818
description: "A LookupRecord data block performs a set of actions on a specific record."
---

# LookupRecord Data Block (Access custom web app)

A **LookupRecord** data block performs a set of actions on a specific record.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/) to build no-code business solutions for the web and mobile devices.
  
> [!NOTE]
> The **LookupRecord** data block is available only in Data Macros.
  
## Setting

The **SetField** action has the following arguments.
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| _In_ <br/> |Yes  <br/> |A string that identifies the record to operate on. The *In* argument can contain the name of the table, a select query, or a SQL statement. |
| _Where Condition_ <br/> |No  <br/> |A string expression used to restrict the range of data on which the **LookupRecord** data block is performed. For example, criteria is often equivalent to the WHERE clause in an SQL expression, without the word WHERE. If criteria is omitted, the **LookupRecord** data block operates on the entire domain specified by the *In* argument. Any field that is included in criteria must also be a field in *In*. |
| _Alias_ <br/> |No  <br/> |A string that provides an alternative name for the record specified by the *In* argument. Often used to shorten the table name for subsequent references to prevent possible ambiguous references. If *Alias*  is not specified, the table or query name will be used as the alias. |
   
## Remarks

If the criteria specified by the *In* and *Where Condition* arguments specifies more than one record, then the **LookupRecord** data block will only operate on the first record.
  
If no record satisfies *Where Condition* or if *In* contains no records, then **LookupRecord** creates a blank record in which all of the fields contain a **Null** value.
  