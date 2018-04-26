---
title: "SQLState Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: cf3b078a-849e-1ad2-cba4-a26160080868

---

# SQLState Property (ADO)

Indicates the SQL state for a given [Error](error-object-ado.md) object. 
  
## Return Value

Returns a five-character **String** value that follows the ANSI SQL standard and indicates the error code. 
  
## Remarks

Use the **SQLState** property to read the five-character error code that the provider returns when an error occurs during the processing of an SQL statement. For example, when using the Microsoft OLE DB Provider for ODBC with a Microsoft SQL Server database, SQL state error codes originate from ODBC, based either on errors specific to ODBC or on errors that originate from Microsoft SQL Server, and are then mapped to ODBC errors. These error codes are documented in the ANSI SQL standard, but may be implemented differently by different data sources. 
  

