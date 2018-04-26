---
title: "NativeError Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9f4d4064-5ee7-20f8-fd54-2cb2eae64d7b

---

# NativeError Property (ADO)

Indicates the provider-specific error code for a given [Error](error-object-ado.md) object. 
  
## Return Value

Returns a **Long** value that indicates the error code. 
  
## Remarks

Use the **NativeError** property to retrieve the database-specific error information for a particular **Error** object. For example, when using the Microsoft ODBC Provider for OLE DB with a Microsoft SQL Server database, native error codes that originate from SQL Server pass through ODBC and the ODBC Provider to the ADO **NativeError** property. 
  

