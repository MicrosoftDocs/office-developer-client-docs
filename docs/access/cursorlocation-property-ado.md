---
title: "CursorLocation Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 8a048bd4-ae25-a555-1c07-14364b7e6560
---

# CursorLocation Property (ADO)

Indicates the location of the cursor service.
  
## Settings And Return Values

Sets or returns a **Long** value that can be set to one of the [CursorLocationEnum](cursorlocationenum.md) values. 
  
## Remarks

This property allows you to choose between various cursor libraries accessible to the provider. Usually, you can choose between using a client-side cursor library or one that is located on the server.
  
This property setting affects connections established only after the property has been set. Changing the **CursorLocation** property has no effect on existing connections. 
  
Cursors returned by the [Execute](http://msdn.microsoft.com/library/af190bd9-7167-df59-29ca-a9a86c4957fd%28Office.15%29.aspx) method inherit this setting. **Recordset** objects will automatically inherit this setting from their associated connections. 
  
This property is read/write on a [Connection](connection-object-ado.md) or a closed [Recordset](recordset-object-ado.md), and read-only on an open **Recordset**. 
  
 **Remote Data Service Usage** When used on a client-side **Recordset** or **Connection** object, the **CursorLocation** property can only be set to **adUseClient**. 
  

