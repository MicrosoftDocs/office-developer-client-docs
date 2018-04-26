---
title: "Source Property (ADO Recordset)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 523ea81e-d011-8d87-436e-084b6eba0908

---

# Source Property (ADO Recordset)

Indicates the data source for a [Recordset](recordset-object-ado.md) object. 
  
## Settings and Return Values

Sets a **String** value or [Command](command-object-ado.md) object reference; returns only a **String** value that indicates the source of the **Recordset**. 
  
## Remarks

Use the **Source** property to specify a data source for a **Recordset** object using one of the following: a **Command** object variable, an SQL statement, a stored procedure, or a table name. 
  
If you set the **Source** property to a **Command** object, the [ActiveConnection](activeconnection-property-ado.md) property of the **Recordset** object will inherit the value of the **ActiveConnection** property for the specified **Command** object. However, reading the **Source** property does not return a **Command** object; instead, it returns the [CommandText](commandtext-property-ado.md) property of the **Command** object to which you set the **Source** property. 
  
If the **Source** property is an SQL statement, a stored procedure, or a table name, you can optimize performance by passing the appropriate  *Options*  argument with the [Open](open-method-ado-recordset.md) method call. 
  
The **Source** property is read/write for closed **Recordset** objects and read-only for open **Recordset** objects. 
  

